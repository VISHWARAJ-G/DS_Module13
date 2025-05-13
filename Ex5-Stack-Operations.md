# Ex5 - Stack Operations

## DATE: 07-03-2025

---

## AIM:
To write a C function to perform push and pop operations of the stack in the infix to postfix conversion.

---

## Algorithm

1. Initialize an empty stack and an empty string for the postfix result.  
2. Scan the infix expression from left to right.  
3. If the character is an operand, append it directly to the postfix expression.  
4. If the character is an operator, perform push or pop based on operator precedence:
   - Pop operators from the stack to the postfix expression while the precedence of the current operator is less than or equal to the operator on the top of the stack.
   - Push the current operator onto the stack.
5. After scanning the expression, pop all remaining operators from the stack to the postfix expression.

---

## Program:

```c
/*
Program to perform push and pop operations of the stack in the infix to postfix conversion
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#include <ctype.h>
#include <string.h>

#define MAX 100

char stack[MAX];
int top = -1;

void push(char ch) {
    stack[++top] = ch;
}

char pop() {
    if (top == -1)
        return -1;
    return stack[top--];
}

int precedence(char op) {
    if (op == '^')
        return 3;
    if (op == '*' || op == '/')
        return 2;
    if (op == '+' || op == '-')
        return 1;
    return 0;
}

void infixToPostfix(char* infix, char* postfix) {
    int i, j = 0;
    char ch;
    for (i = 0; infix[i] != '\0'; i++) {
        ch = infix[i];
        if (isalnum(ch)) {
            postfix[j++] = ch;
        } else if (ch == '(') {
            push(ch);
        } else if (ch == ')') {
            while (stack[top] != '(')
                postfix[j++] = pop();
            pop(); // remove '('
        } else {
            while (top != -1 && precedence(stack[top]) >= precedence(ch))
                postfix[j++] = pop();
            push(ch);
        }
    }
    while (top != -1)
        postfix[j++] = pop();
    postfix[j] = '\0';
}

int main() {
    char infix[MAX], postfix[MAX];
    printf("Enter Infix Expression: ");
    scanf("%s", infix);
    infixToPostfix(infix, postfix);
    printf("Postfix Expression: %s\n", postfix);
    return 0;
}
~~~
```
## Output:
```
Enter Infix Expression: (A+B)*C
Postfix Expression: AB+C*
```
## Result:
Thus, the C program to perform push and pop operations of the stack in the infix to postfix conversion is implemented successfully.
