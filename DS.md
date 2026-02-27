# 1.Operations on STACK of Integers
```
#include <stdio.h>
#define MAX 5
int stack[MAX];
int top = -1;
void push()
{
    int item;
    if(top == MAX - 1)
    {
        printf("Stack Overflow! Cannot push element.\n");
        return;
    }
    printf("Enter element to push: ");
    scanf("%d", &item);
    top++;
    stack[top] = item;
    printf("Element %d pushed onto stack.\n", item);
}
void pop()
{
    if(top == -1)
    {
        printf("Stack Underflow! Cannot pop element.\n");
        return;
    }
    printf("Popped element: %d\n", stack[top]);
    top--;
}
void peek()
{
    if(top == -1)
    {
        printf("Stack is empty. Nothing to peek.\n");
        return;
    }
    printf("Top element is: %d\n", stack[top]);
}
void display()
{
    int i;
    if(top == -1)
    {
        printf("Stack is empty.\n");
        return;
    }
    printf("Stack elements (top to bottom):\n");
    for(i = top; i >= 0; i--)
    {
        printf("%d\n", stack[i]);
    }
}
int main()
{
    int choice;
    while(1)
    {
        printf("\n--- STACK OPERATIONS MENU ---\n");
        printf("1. Push an element\n");
        printf("2. Pop an element\n");
        printf("3. Display Stack Status\n");
        printf("4. Peek top element\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1: push(); break;
            case 2: pop(); break;
            case 3: display(); break;
            case 4: peek(); break;
            case 5: exit(0);break;
            default: printf("Invalid choice! Try again.\n");
        }
    }
return 0;
}
```
# 2.Balancing of Parentheses using a Stack
```
#include <stdio.h>
#include <string.h>
#define MAX 100

char stack[MAX];
int top = -1;

void push(char c) {
    stack[++top] = c;
}

char pop() {
    return stack[top--];
}

int isMatchingPair(char opening, char closing) {
    return (opening == '(' && closing == ')') ||
           (opening == '{' && closing == '}') ||
           (opening == '[' && closing == ']');
}

int isBalanced(const char *expression) {
    int i;
    top = -1;  // Reset stack before checking

    for (i = 0; expression[i] != '\0'; i++) {
        char ch = expression[i];

        if (ch == '(' || ch == '{' || ch == '[') {
            push(ch);
        } 
        else if (ch == ')' || ch == '}' || ch == ']') {
            if (top == -1 || !isMatchingPair(pop(), ch)) {
                return 0;
            }
        }
    }
    return (top == -1);
}

int main() {
    char expression[MAX];

    printf("Enter an expression: ");
    scanf("%s", expression);

    if (isBalanced(expression)) {
        printf("The expression is Balanced.\n");
    } else {
        printf("The expression is Unbalanced.\n");
    }

    return 0;
}
```

