# Ex4 - Evaluation of Prefix Expression

**DATE:06-03-2025**  

---

## AIM:  
To write a C function to evaluate the given prefix expression using stack and print the output of the given prefix expression from the stack inside the function.

---

## Algorithm

1. Start from the end of the prefix expression and move toward the beginning.  
2. For each character in the expression, check if it is an operand or operator.  
3. If it is an operand, push it onto the stack.  
4. If it is an operator, pop two operands from the stack.  
5. Perform the operation with the operator and the two operands.  
6. Push the result back onto the stack.  
7. Repeat this process until the entire prefix expression is scanned.  
8. The final result will be on the top of the stack.

---

## Program:

```c
/*
Program to evaluate the given prefix expression
Developed by: Vishwaraj G.
Register Number: 212223220125
*/

#include <stdio.h>
#include <ctype.h>
#include <math.h>
#include <string.h>

#define MAX 100

int stack[MAX];
int top = -1;

void push(int value) {
    stack[++top] = value;
}

int pop() {
    return stack[top--];
}

int evaluatePrefix(char* expr) {
    int i;
    for (i = strlen(expr) - 1; i >= 0; i--) {
        if (isdigit(expr[i])) {
            push(expr[i] - '0');
        } else {
            int op1 = pop();
            int op2 = pop();
            switch (expr[i]) {
                case '+': push(op1 + op2); break;
                case '-': push(op1 - op2); break;
                case '*': push(op1 * op2); break;
                case '/': push(op1 / op2); break;
                case '^': push(pow(op1, op2)); break;
            }
        }
    }
    return pop();
}

int main() {
    char expr[MAX];
    printf("Enter Prefix Expression: ");
    scanf("%s", expr);
    int result = evaluatePrefix(expr);
    printf("Result: %d\n", result);
    return 0;
}
```
## Output:
```
Enter Prefix Expression: -+7*45+20
Result: 25
```
## Result:
Thus, the C program to evaluate the prefix expression using stack and print the output of the given prefix expression from the stack inside the function is implemented successfully.
