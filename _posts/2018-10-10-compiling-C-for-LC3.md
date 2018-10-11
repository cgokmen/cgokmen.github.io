---
layout: post
title: Compiling C for the LC-3
date: {}
categories:
  - Programming
excerpt: >-
  Being able to run the C language on the LC-3 architecture is a good example of
  the advantages of higher-level languages like C compared to assembly. This  is
  an important learning outcome for CS2110 and thus we explore the compilation
  of C code for the LC3 architecture and the difficulty difference in
  implementing similar programs in both languages.
published: true
---
Being able to run the C language on the LC-3 architecture is a good example
of the advantages of higher-level languages like C compared to assembly. This 
is an important learning outcome for CS2110 and thus we explore the compilation
of C code for the LC3 architecture and the difficulty difference in implementing
similar programs in both languages.

## Initial Setup
These steps assume that you're running the following code on a Mac, but they should work exactly the same on any Linux / Unix platform.

### Install the LC3 Toolkit
Start by building and installing the LC3 toolkit (this installs at `~/.lc3/` but you can add an `--install-path` flag to the `configure` command)
```bash
git clone https://github.com/haplesshero13/lc3tools &&
cd lc3tools &&
./configure &&
make install &&
cd .. &&
rm -rf lc3tools
```

### Install the LC3 to C Compiler
Now build an install the LC3 C Compiler (LCC)
```bash
git clone https://github.com/haplesshero13/lcc-lc3.git &&
cd lcc-lc3 &&
./configure &&
make install &&
cd .. &&
rm -rf lcc-lc3
```

### Get Complx
I suggest Daniel Becker's [CS2110 Docker image](https://github.com/dbecker1/cs2110docker/).
We have a tutorial for this on the CS2110 Canvas, but it's easy enough to install yourself.
The VNC password, when you're done installing, is `cs2110rocks`. The current Mac distro for
complx is not working with this tutorial, so please get the Docker version.

## The routine
### Write a C program
Write a C program (samples are below). We suppose it's called `sample.c`.

### Compile it to assembly
```bash
~/.lc3/lcc -L sample.c -o sample.asm
```

### Run it on Complx
Move the `sample.asm` file to the directory you can see from within your Docker container (`Home > host` in the container). Then launch complx in the container. Go to the File menu and click _Clean Load_. Choose the .asm file and load it. Hit the run button to run your code.

## Sample C Files to Play With
### Percent Calculator
Let `A` be the number found at address `0x4000` and `B` be the number found at address `0x4001`. This program calculates the percent value of `A / B` and stores it in address `0x4002`. Copy this to a file named `percent.c` (longer names will cause problems, do it this way). Then compile using `./lcc -L percent.c -o percent.asm`.

```C
main() {
    unsigned short a = *((unsigned short *) 0x4000U);
    unsigned short b = *((unsigned short *) 0x4001U);

    unsigned short hundred_a = 100 * a;
    unsigned short percent = hundred_a / b;

    *((unsigned short*) 0x4002U) = percent;
    return 0;
}
```

To run it, compile the code as explained above and _Clean Load_ it into complx. Then, before running the program, go into _View -> New View_. Then, in the frame that pops up, go to _View -> Goto Address_ and input `x4000`. Then put in two sample values to addresses `0x4000` and `0x4001` by clicking the _Decimal_ column. For example, put `1` for `0x4000` and `3` for `0x4001`. Then hit _Run_ in the main complx window. The number `33`, corresponding to `1 * 100 / 3`, should appear in address `0x4002`. This is a hard problem to implement manually in assembly due to the multiplication and more importantly, division.

### Selection Sort
Let `n` be the number found at address `0x4000`. This program selection-sorts the `n`-element array starting at address `0x4001` in-place, also printing the sorted numbers to the console. Copy this to a file named `selsort.c` (longer names will cause problems, do it this way). Then compile using `./lcc -L selsort.c -o selsort.asm`.

```C
int main() {
    unsigned short* array = (unsigned short*) 0x4001U;
    unsigned short array_length = *((unsigned short*) 0x4000U);

    unsigned short i, j, min, temp;
    for (i = 0; i < array_length; i++) {
        min = i;
	for (j = i + 1; j < array_length; j++) {
            if (array[j] < array[min]) min = j;
        }

        temp = array[min];
        array[min] = array[i];
        array[i] = temp;

        printf("%d\n", temp);
    }

    return 0;
}
```

To run it, compile the code as explained above and _Clean Load_ it into complx. Then, before running the program, go into _View -> New View_. Then, in the frame that pops up, go to _View -> Goto Address_ and input `x4000`. Then put in a sample array length to addresses `0x4000` by clicking the _Decimal_ column. For example, put `5` for `0x4000`. Then, fill in the following 5 memory addresses, `0x4001` to `0x4005`, with numbers to be sorted, e.g. `1, 3, 2, 8, 5`. Then hit Run - the numbers should be sorted in-place and also printed out to the console in sorted order. This is a hard problem to implement manually in assembly due to the printing and the nested loops.

### The Sieve of Eratosthenes
This program finds the prime numbers less than 100 and prints them into the console. Copy this to a file named `eratos.c` (longer names will cause problems, do it this way). Then compile using `./lcc -L eratos.c -o eratos.asm`.

```C
main() {
    int upTo = 100;
    int isPrime[100];

    int i, curr;
    // Start by assuming all numbers are prime
    for (i = 0; i < upTo; i++) {
        isPrime[i] = 1;
    }

    // Zero and One are not prime
    isPrime[0] = 0;
    isPrime[1] = 0;

    for (curr = 0; curr < upTo; curr++) {
        if (isPrime[curr]) {
            // If the number is prime, then its multiples aren't
            for (i = curr; i * curr < upTo; i++) isPrime[i * curr] = 0;
        }
    }

    // Now print the primes in the range
    for (i = 0; i < upTo; i++) {
        if (isPrime[i]) printf("%d\n", i);
    }

    return 0;
}
```

To run it, compile the code as explained above and _Clean Load_ it into complx. Then hit Run - the numbers should appear in the console in sorted order. This is _NOT_ hard problem to implement manually in assembly :(
