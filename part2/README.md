# Part 2
To read and write RP2040 registers from a console by REPL:

## Read Mode
1. Input 'r'/'R' from the console, to enter read mode.
 
2. Input 8 hexadecimal numbers(0-F) to select register address. 

3. Input another 8 hexadecimal numbers(0-F) to set mask.

4. The register value will be obtained by REPL.

## Write Mode
1. Input 'w'/'W' from the console, to enter write mode.

2. Input 8 hexadecimal numbers(0-F) to select register address. 

3. Input another 8 hexadecimal numbers(0-F) to set mask. 

4. Input 8 hexadecimal numbers(0-F) to set register value

5. The register value will be rewrite by REPL, while value of some registers is not allowed to be written.

## Result
<img width="443" alt="part2" src="https://user-images.githubusercontent.com/114015725/202816772-99746dfd-0275-4bf8-bc2e-8eae6ca7fc17.png">
