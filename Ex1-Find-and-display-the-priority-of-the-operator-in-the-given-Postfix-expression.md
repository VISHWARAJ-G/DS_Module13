# EX 1 Display operator precedence in the infix expression.
## DATE: 03-03-2025
## AIM:
To write a C program to find and display the priority of the operator in the given Postfix expression

## Algorithm
1. Initialize a stack.

2. Loop through each character of the Postfix expression.

3. If the character is an operand, push it to the stack.

4. If the character is an operator, pop two operands from the stack, apply the operator, and push the result back onto the stack.

5. Display the precedence of the operator when it's encountered.

6. The program should handle multiple operators with different precedence.

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
int precedence(char op) {
    if(op == '+' || op == '-') {
        return 1;
    } else if(op == '*' || op == '/') {
        return 2;
    } else if(op == '^') {
        return 3;
    }
    return -1; // Invalid operator
}
void evaluatePostfix(char* expression) {
    int i = 0;
    while (expression[i] != '\0') {
        if (isdigit(expression[i])) {
            // Operand, no action needed
            i++;
        } else if (expression[i] == '+' || expression[i] == '-' || expression[i] == '*' || expression[i] == '/' || expression[i] == '^') {
            // Operator, display its precedence
            printf("Operator: %c, Precedence: %d\n", expression[i], precedence(expression[i]));
            i++;
        } else {
            printf("Invalid character encountered.\n");
            return;
        }
    }
}
int main() {
    // Sample Postfix expression
    char expression[] = "23*4+5^";
    
    printf("Postfix Expression: %s\n", expression);
    evaluatePostfix(expression);

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/98b5b3f0-d798-4190-8fbe-b32818c06571)


## Result:
Thus the C program to find and display the priority of the operator in the given Postfix expression is implemented successfully
