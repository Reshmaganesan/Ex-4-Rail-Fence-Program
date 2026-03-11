# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

 To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <stdlib.h>


int cmpfunc(const void *a, const void *b) {
    return (*(char *)a - *(char *)b);
}

int main() {
    char plaintext[100], keyword[20];
    char matrix[20][20];  
    int lenText, lenKey, rows, k = 0;

   
    printf("Enter the plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0'; 
    lenText = strlen(plaintext);

   
    printf("Enter the keyword: ");
    scanf("%s", keyword);
    lenKey = strlen(keyword);

   
    rows = (lenText + lenKey - 1) / lenKey; 
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < lenKey; j++) {
            if (k < lenText)
                matrix[i][j] = plaintext[k++];
            else
                matrix[i][j] = 'X'; 
        }
    }


    int order[20];
    for (int i = 0; i < lenKey; i++)
        order[i] = i;

  
    for (int i = 0; i < lenKey - 1; i++) {
        for (int j = i + 1; j < lenKey; j++) {
            if (keyword[j] < keyword[i]) {
                char temp = keyword[i];
                keyword[i] = keyword[j];
                keyword[j] = temp;

                int tmp = order[i];
                order[i] = order[j];
                order[j] = tmp;
            }
        }
    }

  
    printf("Cipher Text: ");
    for (int c = 0; c < lenKey; c++) {
        int col = order[c];
        for (int r = 0; r < rows; r++) {
            printf("%c", matrix[r][col]);
        }
    }
    printf("\n");

    return 0;
}
```



# OUTPUT

<img width="569" height="342" alt="Screenshot 2026-03-11 152711" src="https://github.com/user-attachments/assets/fd560d18-e3c8-45f7-8e62-fe92e87f1db7" />


# RESULT
Thus, the C program to implement the Rail Fence transposition technique was written and
executed successfully, and the cipher text was generated correctly. 


