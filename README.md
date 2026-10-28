# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

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

void rail_fence(char *s, int rails, int decrypt) {
    int len = strlen(s);
    if (rails <= 1 || rails >= len) return;

    int cycle = 2 * (rails - 1);
    char out[len + 1];

    if (!decrypt) {
        int k = 0;
        for (int r = 0; r < rails; r++) {
            for (int i = 0; i < len; i++) {
                int pos = i % cycle;
                if (pos == r || pos == cycle - r) out[k++] = s[i];
            }
        }
    } else {
        int k = 0;
        for (int r = 0; r < rails; r++) {
            for (int i = 0; i < len; i++) {
                int pos = i % cycle;
                if (pos == r || pos == cycle - r) out[i] = s[k++];
            }
        }
    }
    out[len] = '\0';
    strcpy(s, out);
}

int main(void) {
    char s[256], m;
    int r;
    printf("Text: ");   scanf(" %[^\n]", s);
    printf("Rails: ");  scanf("%d", &r);
    printf("(E/D): ");  scanf(" %c", &m);

    rail_fence(s, r, m == 'd' || m == 'D');
    printf("Result: %s\n", s);
    return 0;
}
```
# OUTPUT
<img width="1919" height="1094" alt="image" src="https://github.com/user-attachments/assets/47e1224f-6562-40db-aa7f-5aedd95c48ee" />

# RESULT
Thus the program for Rail fence program has been successfully implemented using C program
