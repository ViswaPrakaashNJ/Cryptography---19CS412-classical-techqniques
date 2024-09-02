# Cryptography---19CS412-classical-techqniques
# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To encrypt and decrypt the given message by using Ceaser Cipher encryption algorithm.


## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

1.	In Ceaser Cipher each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.
2.	For example, with a left shift of 3, D would be replaced by A, E would become B, and so on.
3.	The encryption can also be represented using modular arithmetic by first transforming the letters into numbers, according to the   
    scheme, A = 0, B = 1, Z = 25.
4.	Encryption of a letter x by a shift n can be described mathematically as,
                       En(x) = (x + n) mod26
5.	Decryption is performed similarly,
                       Dn (x)=(x - n) mod26


## PROGRAM:
```
#include<stdio.h>
#include<string.h>
#include<ctype.h>

int main()
{
    char plain[10], cipher[10];
    int key, i, length;

    // Input the plain text
    printf("\nEnter the plain text: ");
    scanf("%s", plain);

    // Input the key value
    printf("\nEnter the key value: ");
    scanf("%d", &key);

    // Display the original plain text
    printf("\n\nPLAIN TEXT: %s", plain);

    // Encrypt the plain text
    printf("\n\nENCRYPTED TEXT: ");
    length = strlen(plain);
    for(i = 0; i < length; i++)
    {
        cipher[i] = plain[i] + key;

        // Handle wrap-around for uppercase letters
        if (isupper(plain[i]) && (cipher[i] > 'Z'))
            cipher[i] = cipher[i] - 26;

        // Handle wrap-around for lowercase letters
        if (islower(plain[i]) && (cipher[i] > 'z'))
            cipher[i] = cipher[i] - 26;

        // Print the encrypted character
        printf("%c", cipher[i]);
    }

    // Decrypt the cipher text
    printf("\n\nAFTER DECRYPTION: ");
    for(i = 0; i < length; i++)
    {
        plain[i] = cipher[i] - key;

        // Handle wrap-around for uppercase letters
        if (isupper(cipher[i]) && (plain[i] < 'A'))
            plain[i] = plain[i] + 26;

        // Handle wrap-around for lowercase letters
        if (islower(cipher[i]) && (plain[i] < 'a'))
            plain[i] = plain[i] + 26;

        // Print the decrypted character
        printf("%c", plain[i]);
    }

    return 0;
}

```


## OUTPUT:

![Screenshot 2024-09-02 135653](https://github.com/user-attachments/assets/73fb3a8f-4a03-4231-8ef3-85ea5fe46766)


## RESULT:
The program is executed successfully
