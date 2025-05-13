# Ex2 Conversion of the infix expression into postfix expression
## DATE: 04-03-2025
## AIM:
To write a C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule.

## Algorithm
1. Initialize an empty stack to store operators and an empty string to store the resulting postfix expression.

2. Scan the infix expression from left to right:  
   i. If the character is an operand (i.e., a number or variable), directly append it to the postfix expression.  
   ii. If the character is an opening parenthesis `(`, push it onto the stack.  
   iii. If the character is a closing parenthesis `)`, pop from the stack to the postfix expression until an opening parenthesis is encountered. Discard the opening parenthesis.

3. If the character is an operator (`+`, `-`, `*`, `/`, `^`):  
   i. While the stack is not empty and the precedence of the top operator on the stack is greater than or equal to the current operator, pop the top operator from the stack and append it to the postfix expression.  
   ii. Push the current operator onto the stack.

4. After processing all characters of the infix expression, pop all remaining operators from the stack and append them to the postfix expression.

5. Return the postfix expression, which is now fully constructed.

## Program:
```
/*
Program to convert the infix expression into postfix expression
Developed by: Vishwaraj G.
RegisterNumber:  212223220125
*/
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

// Function to return precedence of operators
int precedence(char op) {
    if(op == '+' || op == '-') {
        return 1;
    } else if(op == '*' || op == '/') {
        return 2;
    } else if(op == '^') {
        return 3;
    }
    return -1;
}

// Function to check if the character is an operator
int isOperator(char ch) {
    return (ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '^');
}

// Function to perform infix to postfix conversion
void infixToPostfix(char* infix, char* postfix) {
    int i = 0, j = 0;
    char stack[100]; // stack to store operators
    int top = -1; // stack pointer

    while (infix[i] != '\0') {
        if (isalnum(infix[i])) {
            // If the character is an operand, add it to the postfix expression
            postfix[j++] = infix[i++];
        }
        else if (infix[i] == '(') {
            // If the character is '(', push it to the stack
            stack[++top] = infix[i++];
        }
        else if (infix[i] == ')') {
            // If the character is ')', pop from the stack to the postfix expression until '('
            while (top != -1 && stack[top] != '(') {
                postfix[j++] = stack[top--];
            }
            top--; // Remove '(' from stack
            i++;
        }
        else if (isOperator(infix[i])) {
            // If the character is an operator, pop operators with higher or equal precedence
            while (top != -1 && precedence(stack[top]) >= precedence(infix[i])) {
                postfix[j++] = stack[top--];
            }
            stack[++top] = infix[i++];
        }
    }

    // Pop all remaining operators from the stack
    while (top != -1) {
        postfix[j++] = stack[top--];
    }
    postfix[j] = '\0'; // Null-terminate the postfix expression
}

int main() {
    char infix[100], postfix[100];

    // Input infix expression
    printf("Enter an infix expression: ");
    fgets(infix, sizeof(infix), stdin);
    
    // Remove newline character if present
    size_t len = strlen(infix);
    if (infix[len - 1] == '\n') {
        infix[len - 1] = '\0';
    }

    // Convert infix to postfix
    infixToPostfix(infix, postfix);

    // Display the result
    printf("Postfix Expression: %s\n", postfix);

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/f8157b81-6566-455f-a665-be6e78f9e24a)


## Result:
Thus, the C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule is implemented successfully.
