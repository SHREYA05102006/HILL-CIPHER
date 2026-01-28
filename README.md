# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. 

STEP-2: Split the plain text into groups of length three. 

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```py
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main()
{
    int key[3][3];
    int i, j, k;
    char plain[100], cipher[100];
    int p[3], c[3];
    int len;

    printf("Enter 3x3 key matrix (9 numbers):\n");
    for(i = 0; i < 3; i++)
    {
        for(j = 0; j < 3; j++)
        {
            scanf("%d", &key[i][j]);
        }
    }

    printf("Enter plaintext (only alphabets): ");
    scanf("%s", plain);

    len = strlen(plain);

    // If length not multiple of 3, pad with 'X'
    while(len % 3 != 0)
    {
        plain[len] = 'X';
        len++;
    }
    plain[len] = '\0';

    for(i = 0; i < len; i += 3)
    {
        // Convert letters to numbers
        for(j = 0; j < 3; j++)
        {
            p[j] = toupper(plain[i+j]) - 'A';
        }

        // Matrix multiplication
        for(j = 0; j < 3; j++)
        {
            c[j] = 0;
            for(k = 0; k < 3; k++)
            {
                c[j] += key[j][k] * p[k];
            }
            c[j] = c[j] % 26;
        }

        // Convert back to letters
        for(j = 0; j < 3; j++)
        {
            cipher[i+j] = c[j] + 'A';
        }
    }

    cipher[len] = '\0';

    printf("Cipher Text: %s\n", cipher);

    return 0;
}

```

## OUTPUT
<img width="450" height="253" alt="image" src="https://github.com/user-attachments/assets/829412a8-905d-4afd-a015-a8919e5bb448" />

## RESULT
Thus, the Hill Cipher substitution technique was successfully implemented using a 3×3 key matrix in C. The plaintext was encrypted by matrix multiplication and modulo 26 operation to produce the corresponding ciphertext.
