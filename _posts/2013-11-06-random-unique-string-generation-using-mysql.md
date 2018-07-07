---
id: 678
title: 'Random &#038; Unique String Generation Using MySQL'
date: 2013-11-06T00:05:06+00:00
author: Cem Gokmen
layout: post
guid: http://www.cemgokmen.com/?p=678
permalink: /random-unique-string-generation-using-mysql/
categories:
  - Programming
  - Technology
tags:
  - Lua
  - MTA
  - MySQL
---
Good evening,  
  
I&#8217;m back with the first ever informative blog post!  
  
So recently I had rewritten this vehicles script for our Multi Theft Auto server WhySoSerious:RPG. The script was a static vehicles script that read data off of a MySQL Table. What the new version did was it would assign a unique license plate to each newly generated vehicle. However, the problem with this script was that it used Lua to generate the strings and query the vehicles&#8217; MySQL table one by one for each generated string, which lagged the server and increased the required number of queries we needed to do before INSERTing the new vehicle into the database.  
  
So I came up with a MySQL function that would generate a 8-char string and check if it already existed in the table, as many times as needed until a previously unused string is found. Then the function would simply return the found value, which would allow the function to be used within other queries.  
  
Here&#8217;s the function code:  


<pre class="brush: sql; title: ; notranslate" title="">DELIMITER $$
CREATE FUNCTION GenerateLicensePlate()
	RETURNS VARCHAR(8)

	BEGIN
	DECLARE plate VARCHAR(8) DEFAULT "" ;
	WHILE LENGTH(plate) = 0 DO
		SELECT concat(substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1),
      	        substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1),
      	        substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1),
            	substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1),
             	substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1),
             	substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1),
              	substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1),
              	substring('ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', rand()*36+1, 1)
             	) into @newplate;
   
  		SET @rcount = -1;
  		SELECT COUNT(*) INTO @rcount FROM `vehicles` WHERE `plate` = @newplate ;
   
   		IF @rcount = 0 THEN
   			SET plate = @newplate ;
   		END IF ;
	END WHILE ;

	RETURN plate ;
	END$$
DELIMITER ;

</pre>

  
  
I used <a href="http://stackoverflow.com/a/16738136/1333566" target="_blank">this</a> response I got on a previous StackOverflow question I posted about it, and came up with the rest myself. Turns out those MySQL manuals are actually pretty handy when you try to read them.
  
  
  

  
You can read a random plate by using this query:  


<pre class="brush: sql; title: ; notranslate" title="">SELECT GenerateLicensePlate();

</pre>

  
  

  
And you can implement it within your insert like this:  


<pre class="brush: sql; title: ; notranslate" title="">INSERT INTO `vehicles`(`name`, `plate`) VALUES ("Coolcar", GenerateLicensePlate());

</pre>

  
  

  
I hope it&#8217;s useful, comment for any questions!