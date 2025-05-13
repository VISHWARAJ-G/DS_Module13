# EX3 - Implementation of Tower of Hanoi

## DATE: 05-03-2025

---

## AIM:  
To write a C program to implement Tower of Hanoi.

---

## Algorithm

1. If there is only one disk, move it directly from source to destination.  
2. Recursively move (n-1) disks from the source rod to the auxiliary rod.  
3. Move the nth disk from the source rod to the destination rod.  
4. Recursively move the (n-1) disks from the auxiliary rod to the destination rod.  
5. Repeat the above steps until all disks are moved from the source to the destination.

---

## Program:

```c
/*
Program to implement Tower of Hanoi
Developed by: Vishwaraj G
Register Number: 21222322o125
*/

#include <stdio.h>

void towerOfHanoi(int n, char source, char destination, char auxiliary) {
    if (n == 1) {
        printf("Move disk 1 from %c to %c\n", source, destination);
        return;
    }
    towerOfHanoi(n - 1, source, auxiliary, destination);
    printf("Move disk %d from %c to %c\n", n, source, destination);
    towerOfHanoi(n - 1, auxiliary, destination, source);
}

int main() {
    int n;
    printf("Enter number of disks: ");
    scanf("%d", &n);
    printf("The sequence of moves:\n");
    towerOfHanoi(n, 'A', 'C', 'B'); // A = source, C = destination, B = auxiliary
    return 0;
}
```
## Output:
```
Enter number of disks: 3  
The sequence of moves:  
Move disk 1 from A to C  
Move disk 2 from A to B  
Move disk 1 from C to B  
Move disk 3 from A to C  
Move disk 1 from B to A  
Move disk 2 from B to C  
Move disk 1 from A to C  

```

## Result:
Thus, the C program to implement Tower of Hanoi using recursion is implemented successfully.
