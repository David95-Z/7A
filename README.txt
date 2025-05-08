#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char plain[100], cipher[100];
    int key, i, length;

    // Get input from user
    printf("Enter the plain text: ");
    scanf("%s", plain);

    printf("Enter the key value (number): ");
    scanf("%d", &key);

    length = strlen(plain);

    // Encryption
    printf("\nPLAIN TEXT: %s", plain);
    printf("\nENCRYPTED TEXT: ");
    for (i = 0; i < length; i++) {
        char ch = plain[i];

        // Shift character by key
        if (isalpha(ch)) {
            if (isupper(ch)) {
                cipher[i] = ((ch - 'A' + key) % 26) + 'A';
            } else {
                cipher[i] = ((ch - 'a' + key) % 26) + 'a';
            }
        } else {
            cipher[i] = ch; // Non-alphabetic characters remain unchanged
        }

        printf("%c", cipher[i]);
    }
    cipher[length] = '\0';

    // Decryption
    printf("\nDECRYPTED TEXT: ");
    for (i = 0; i < length; i++) {
        char ch = cipher[i];

        if (isalpha(ch)) {
            if (isupper(ch)) {
                plain[i] = ((ch - 'A' - key + 26) % 26) + 'A';
            } else {
                plain[i] = ((ch - 'a' - key + 26) % 26) + 'a';
            }
        } else {
            plain[i] = ch;
        }

        printf("%c", plain[i]);
    }
    plain[length] = '\0';

    return 0;
}
