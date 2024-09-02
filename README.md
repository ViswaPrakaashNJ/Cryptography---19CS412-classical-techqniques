# Cryptography---19CS412-classical-techqniques
# PlayFair Cipher
Playfair Cipher using with different key values

# AIM:

To implement a program to encrypt a plain text and decrypt a cipher text using play fair Cipher substitution technique.

 
## DESIGN STEPS:

### Step 1:

Design of PlayFair Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

ALGORITHM DESCRIPTION:
The Playfair cipher uses a 5 by 5 table containing a key word or phrase. To generate the key table, first fill the spaces in the table with the letters of the keyword, then fill the remaining spaces with the rest of the letters of the alphabet in order (usually omitting "Q" to reduce the alphabet to fit; other versions put both "I" and "J" in the same space). The key can be written in the top rows of the table, from left to right, or in some other pattern, such as a spiral beginning in the upper-left-hand corner and ending in the centre.
The keyword together with the conventions for filling in the 5 by 5 table constitutes the cipher key. To encrypt a message, one would break the message into digrams (groups of 2 letters) such that, for example, "HelloWorld" becomes "HE LL OW OR LD", and map them out on the key table. Then apply the following 4 rules, to each pair of letters in the plaintext:
1.	If both letters are the same (or only one letter is left), add an "X" after the first letter. Encrypt the new pair and continue. Some   
   variants of Playfair use "Q" instead of "X", but any letter, itself uncommon as a repeated pair, will do.
2.	If the letters appear on the same row of your table, replace them with the letters to their immediate right respectively (wrapping 
   around to the left side of the row if a letter in the original pair was on the right side of the row).
3.	If the letters appear on the same column of your table, replace them with the letters immediately below respectively (wrapping around 
   to the top side of the column if a letter in the original pair was on the bottom side of the column).
4.	If the letters are not on the same row or column, replace them with the letters on the same row respectively but at the other pair of 
   corners of the rectangle defined by the original pair. The order is important – the first letter of the encrypted pair is the one that 
    lies on the same row as the first letter of the plaintext pair.
To decrypt, use the INVERSE (opposite) of the last 3 rules, and the 1st as-is (dropping any extra "X"s, or "Q"s that do not make sense in the final message when finished).


## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#define SIZE 5
void generateKeyTable(char key[], char keyTable[SIZE][SIZE]) {
int dicty[26] = {0};
int i, j, k = 0, len = strlen(key);
for (i = 0; i < len; i++) {
    if (key[i] != 'j' && dicty[key[i] - 'a'] == 0) {
        keyTable[k / SIZE][k % SIZE] = key[i];
        dicty[key[i] - 'a'] = 1;
        k++;
        
    }
    
}
for (i = 0; i < 26; i++) {
    if (i != 9 && dicty[i] == 0) { // skip 'j'
    keyTable[k / SIZE][k % SIZE] = (char)(i + 'a');
    k++;
        
    }
    
}
}
void prepareText(char text[], char preparedText[]) {
int i, j = 0, len = strlen(text);
for (i = 0; i < len; i++) {
    text[i] = tolower(text[i]);
    if (text[i] == 'j') {
        text[i] = 'i';
        
    }
}
for (i = 0; i < len; i++) {
    if (isalpha(text[i])) {
        preparedText[j++] = text[i];
        
    }
}
preparedText[j] = '\0';
for (i = 0; i < j; i += 2) {
    if (preparedText[i] == preparedText[i + 1]) {
        memmove(preparedText + i + 2, preparedText + i + 1, j - i +1);
        preparedText[i + 1] = 'x';
        j++;
        
    }
}
if (strlen(preparedText) % 2 != 0) {
    preparedText[j++] = 'x';
    preparedText[j] = '\0';
}
}
void searchPosition(char keyTable[SIZE][SIZE], char a, char b, int
pos[]) {
int i, j;
if (a == 'j') a = 'i';
if (b == 'j') b = 'i';
for (i = 0; i < SIZE; i++) {
    for (j = 0; j < SIZE; j++) {
        if (keyTable[i][j] == a) {
            pos[0] = i;
            pos[1] = j;
}
if (keyTable[i][j] == b) {
    pos[2] = i;
    pos[3] = j;
    
}
}
}
}
void encryptOrDecrypt(char text[], char keyTable[SIZE][SIZE], int mode)
{
int i, pos[4], len = strlen(text);
for (i = 0; i < len; i += 2) 
{
    searchPosition(keyTable, text[i], text[i + 1], pos);
    if (pos[0] == pos[2]) {
        text[i] = keyTable[pos[0]][(pos[1] + mode + SIZE) % SIZE];
        text[i + 1] = keyTable[pos[2]][(pos[3] + mode + SIZE) %
        SIZE];
        
    } 
    else if (pos[1] == pos[3]) {text[i] = keyTable[(pos[0] + mode + SIZE) % SIZE][pos[1]];
    text[i + 1] = keyTable[(pos[2] + mode + SIZE) % SIZE]
    [pos[3]];
        
    }
    else {
        text[i] = keyTable[pos[0]][pos[3]];
        text[i + 1] = keyTable[pos[2]][pos[1]];
        
    }
    
}
}
int main() {
char key[30], text[100], preparedText[100], keyTable[SIZE][SIZE];
int choice;
printf("Enter the key: ");
gets(key);
generateKeyTable(key, keyTable);
printf("Enter the text: ");
gets(text);
prepareText(text, preparedText);
printf("Enter 1 to encrypt or 2 to decrypt: ");
scanf("%d", &choice);
if (choice == 1) {
    encryptOrDecrypt(preparedText, keyTable, 1);
    printf("Encrypted text: %s\n", preparedText);
} else if (choice == 2) {
    encryptOrDecrypt(preparedText, keyTable, -1);
    printf("Decrypted text: %s\n", preparedText);
} else {
    printf("Invalid choice!\n");
}
return 0;
}
```

## OUTPUT:

ENCRYPTION:

![image](https://github.com/user-attachments/assets/913b1c27-0291-4f78-b692-c36ab3a0be3c)


DECRYPTION:

![Screenshot 2024-09-02 125051](https://github.com/user-attachments/assets/a7a2c887-73a3-4d22-8862-560a85e38c57)



## RESULT:
The program is executed successfully


---------------------------
