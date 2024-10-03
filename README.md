HATFD1005 
Longest Palindromic Substring 
Write a program to find the longest palindromic substring in a given string without using any built-in substring or reverse functions. For example, for input "babad", the output should be "bab" or "aba". 
Instructions: Avoid using any string handling libraries. Implement a solution that checks all substrings manually. 
Code for following program:
#include <stdio.h>
int mstrlen(char s[]) {
    int len = 0;
    while (s[len] != '\0') {
        len++;
    }
    return len;
}
int isPalindrome(char s[], int start, int end) {
    while (start < end) {
        if (s[start] != s[end]) {
            return 0;
        }
        start++;
        end--;
    }
    return 1;
}
void longestPalindrome(char s[], char result[]) {
    int n = mstrlen(s);
    int maxLen = 0;
    int strtInd = 0;
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            if (isPalindrome(s, i, j)) {
                int currlen = j - i + 1;
                if (currlen > maxLen) {
                    maxLen = currlen;
                    strtInd = i;
                }
            }
        }
    }
    for (int i = 0; i < maxLen; i++) {
        result[i] = s[strtInd + i];
    }
    result[maxLen] = '\0';
}
int main() {
    char s[110];
    char result[110];
    scanf("%s", s);
    longestPalindrome(s, result);
    printf("Longest palindromic substring is : %s", result);
    
}

Output:
 ![Screenshot 2024-10-03 213216](https://github.com/user-attachments/assets/74c7e9dc-38b6-491f-a1ef-f21e8608a016)

