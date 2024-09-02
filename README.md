# Cryptography---19CS412-classical-techqniques
# Vigenere Cipher
Vigenere Cipher using with different key values

# AIM:

To develop a simple C program to implement Vigenere Cipher.

## DESIGN STEPS:

### Step 1:

Design of Vigenere Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 
ALGORITHM DESCRIPTION:
The Vigenere cipher is a method of encrypting alphabetic text by using a series of different Caesar ciphers based on the letters of a keyword. It is a simple form of polyalphabetic substitution.To encrypt, a table of alphabets can be used, termed a Vigenere square, or Vigenere table. It consists of the alphabet written out 26 times in different rows, each alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses a different alphabet from one of the rows used. The alphabet at each point depends on a repeating keyword.



## PROGRAM:
```
#include <stdio.h>
#include<conio.h>
#include <ctype.h>
#include <string.h>
void encipher();
void decipher();
int main()
{
    int choice;
    while(1)
    {
        printf("\n1. Encrypt Text");
        printf("\n2. Decrypt Text");
        printf("\n3. Exit");
        printf("\n\nEnter Your Choice : ");
        scanf("%d",&choice);
        if(choice == 3)
        exit(0);
        else if(choice == 1)
        encipher();
        else if(choice == 2)
        decipher();
        else
        printf("Please Enter Valid Option.");
        
    }
}
void encipher()
{
unsigned int i,j;
char input[50],key[10];
printf("\n\nEnter Plain Text: ");
scanf("%s",input);
printf("\nEnter Key Value: ");
scanf("%s",key);
printf("\nResultant Cipher Text: ");
OUTPUT : Encryption:
for(i=0,j=0;i<strlen(input);i++,j++)
{
    if(j>=strlen(key))
    { 
        j=0;
        
    }
    printf("%c",65+(((toupper(input[i])-65)+(toupper(key[j])-65))%26));
}}
void decipher()
{
unsigned int i,j;
char input[50],key[10];
int value;
printf("\n\nEnter Cipher Text: ");
scanf("%s",input);
printf("\n\nEnter the key value: ");
scanf("%s",key);
for(i=0,j=0;i<strlen(input);i++,j++)
{
    if(j>=strlen(key))
    { 
        j=0; 
        
    }
    value = (toupper(input[i])-64)-(toupper(key[j])-64);
    if( value < 0)
    { 
        value = value * -1;
        
    }
    printf("%c",65 + (value % 26));
    
}
return 0;
}
```

## OUTPUT:

Encryption:

![image](https://github.com/user-attachments/assets/63ab8848-32dd-4551-957c-dc97080f4c30)


Decryption:

![Screenshot 2024-09-02 132730](https://github.com/user-attachments/assets/52b099c1-d22c-407e-9844-3040e9c3f7d3)


## RESULT:
The program is executed successfully


-------------------------------------------------
