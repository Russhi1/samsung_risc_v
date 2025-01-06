 We write a C program that adds numbers from 1 to 'n'.
  Then we write down our C code in the editor and save it as {filename.c} file.

  
### Code

```
# include <stdio.h.>

int main() {
    int i, sum= 0, n= 5;
    for (i=o; i<=n; ++i) {
    sum +=i;
    }
    printf("Sum of the numbers from 1 to %d is %d\n", n,sum);
    return 0;
}
```
![Screenshot 2025-01-06 144734](https://github.com/user-attachments/assets/0710bbb6-707c-413a-9e8a-534197fa7240)

* After saving the file we write down the command
` gcc {filename.c} `
` ./a.out`



![Screenshot 2025-01-06 144839](https://github.com/user-attachments/assets/7bd34838-b9ab-49f0-9a58-f9dd3bce37da)

* We write another command and run it.
` riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o {filename}.o {filename}.c`

![Screenshot 2025-01-06 145127](https://github.com/user-attachments/assets/4158c0c1-ea15-430a-b817-c123283ea445)

* We go to another tab and see the assembly code of the program

`riscv64-unknown-elf-objdump -d {filename}.o`


![Screenshot 2025-01-06 150339](https://github.com/user-attachments/assets/dfdbe732-a0c2-4cec-8f87-f92a81641277)

* Then we type another command

  ` riscv64-unknown-elf-objdump -d {filename}.o | less `

This will give us the section of the code but we require only the main section.
* Then we locate the byte address of the main section.

## Finding the number of instructions

* We add the last instruction with 4 to get the next address.
  As it is byte instructions it always increments by 4.


![Screenshot 2025-01-06 150646](https://github.com/user-attachments/assets/195b7756-3008-4ef8-8835-77a08ae68356)

### To count the number of instructions

* The first instruction is subtracted from the first instruction of the previous address and then divided by 4.


![Screenshot 2025-01-06 151232](https://github.com/user-attachments/assets/0282cd2d-ab6f-4873-94f6-b39a8e3c1840)

hen we get the number of instructions in the DEC section.



* We run the same command but instead of `O1`  we use
  ` Ofast `
  ` riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o {filename}.o {filename}.c`

  * We run the same command and search for the main again
  * Then we again calculate the number of instructions.
 

![Screenshot 2025-01-06 151535](https://github.com/user-attachments/assets/4ed0bae2-1b5f-4eec-8116-74d134046153)






