## 1.Operations on STACK of Integers
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
## 2.Balancing of Parentheses using a Stack
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
    top = -1;  

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
## 3.Infix To Postfix Expression
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define MAX 50

char stack[MAX];
int top = -1;

void push(char c) {
    stack[++top] = c;
}

char pop() {
    return stack[top--];
}

char peek() {
    return stack[top];
}

int isEmpty() {
    return top == -1;
}

int precedence(char c) {
    if (c == '*' || c == '/') return 2;
    if (c == '+' || c == '-') return 1;
    return 0;
}

int isOperator(char c) {
    return (c == '+' || c == '-' || c == '*' || c == '/');
}

void infixToPostfix(char infix[], char postfix[]) {
    int i, j = 0;
    char ch;

    for (i = 0; infix[i] != '\0'; i++) {
        ch = infix[i];

        if (isalnum(ch)) {
            postfix[j++] = ch;
        }
        else if (ch == '(') {
            push(ch);
        }
        else if (ch == ')') {
            while (!isEmpty() && peek() != '(')
                postfix[j++] = pop();
            pop(); // remove '('
        }
        else if (isOperator(ch)) {
            while (!isEmpty() && precedence(peek()) >= precedence(ch))
                postfix[j++] = pop();
            push(ch);
        }
    }

    while (!isEmpty())
        postfix[j++] = pop();

    postfix[j] = '\0';
}

int main() {
    char infix[MAX], postfix[MAX];

    printf("Enter infix expression: ");
    scanf("%s", infix);

    infixToPostfix(infix, postfix);

    printf("Infix   : %s\n", infix);
    printf("Postfix : %s\n", postfix);

    return 0;
}
```
## 4.Postfix Evaluation
```
#include <stdio.h>
#include <stdlib.h>

#define MAX_SIZE 10
int stack[MAX_SIZE];
int top = -1;
void push(int item) {
    
	stack[++top] = item;
}
int pop() {
    return stack[top--];
}
int is_operator(char symbol) {
    if (symbol == '+' || symbol == '-' || symbol == '*' || symbol == '/'){
	
        return 1;}
    return 0;
}
int evaluate(char *expression) {
    int i = 0;
    char symbol;
    int operand1, operand2, result;

    while ((symbol = expression[i++]) != '\0') {
        if (symbol >= '0' && symbol <= '9') {
            push(symbol - '0');
        }
        else if (is_operator(symbol)) {
            operand2 = pop();
            operand1 = pop();

            switch (symbol) {
                case '+': result = operand1 + operand2; break;
                case '-': result = operand1 - operand2; break;
                case '*': result = operand1 * operand2; break;
                case '/': result = operand1 / operand2; break;
            }

            push(result);
        }
    }
    return pop();
}
int main() {
    char expression[MAX_SIZE];
    printf("Enter postfix expression: ");
    scanf("%s", expression);
    printf("Result = %d\n", evaluate(expression));
    return 0;
}
```
## 5.Linear QUEUE of Integers
```
#include <stdio.h>
#include <stdlib.h>
#define SIZE 5

int Q[SIZE];
int front = -1, rear = -1;

void enqueue() {
    int item;
    if(rear == SIZE-1) {
        printf("Queue Overflow\n");
        return;
    }
    if(front == -1) front = 0;

    printf("Enter element: ");
    scanf("%d", &item);

    Q[++rear] = item;
}

void dequeue() {
    if(front == -1 || front > rear) {
        printf("Queue Underflow\n");
        return;
    }
    printf("Deleted element: %d\n", Q[front++]);

    if(front > rear){
        front = rear = -1;
    }
}

void display() {
    int i;
    if(front == -1) {
        printf("Queue is empty\n");
        return;
    }
    printf("Queue elements: ");
    for(i = front; i <= rear; i++)
        printf("%d ", Q[i]);
    printf("\n");
}

int main() {
    int ch;
    while(1) {
        printf("\n1.Enqueue  2.Dequeue  3.Display  4.Exit\n");
        printf("Enter choice: ");
        scanf("%d", &ch);

        switch(ch) {
            case 1: enqueue(); break;
            case 2: dequeue(); break;
            case 3: display(); break;
            case 4: exit(0);
            default: printf("Invalid choice\n");
        }
    }
}
```
## 6.Circular QUEUE of Integers
```
#include <stdio.h>
#define SIZE 5

int Q[SIZE];
int Front = -1, Rear = -1;

void enqueue() {
    int item;

    if((Rear + 1) % SIZE == Front) {
        printf("Queue Overflow\n");
        return;
    }

    printf("Enter element: ");
    scanf("%d", &item);

    if(Front == -1)
        Front = 0;

    Rear = (Rear + 1) % SIZE;
    Q[Rear] = item;
}

void dequeue() {
    if(Front == -1) {
        printf("Queue Underflow\n");
        return;
    }

    printf("Deleted element: %d\n", Q[Front]);

    if(Front == Rear)
        Front = Rear = -1;
    else
        Front = (Front + 1) % SIZE;
}

void display() {
    if(Front == -1) {
        printf("Queue is empty\n");
        return;
    }

    int i = Front;
    printf("Queue elements: ");
    while(1) {
        printf("%d ", Q[i]);
        if(i == Rear)
            break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    int ch;
    while(1) {
        printf("\n1.Enqueue 2.Dequeue 3.Display 4.Exit\n");
        printf("Enter choice: ");
        scanf("%d", &ch);

        switch(ch) {
            case 1: enqueue(); break;
            case 2: dequeue(); break;
            case 3: display(); break;
            case 4: return 0;
            default: printf("Invalid choice\n");
        }
    }
}
```
## 7.Priority Queue
```
#include <stdio.h>
#include <stdlib.h>

#define MAX 5

int pri_que[MAX];
int front = -1, rear = -1;

void check(int data)
{
    int i, j;
    for (i = 0; i <= rear; i++)
    {
        if (data <= pri_que[i])
        {
            for (j = rear + 1; j > i; j--)
            {
                pri_que[j] = pri_que[j - 1];
            }
            pri_que[i] = data;
            return;
        }
    }
    pri_que[i] = data;
}

void insert_by_priority(int data)
{
    if (rear >= MAX - 1)
    {
        printf("\nQueue Overflow");
        return;
    }

    if (front == -1 && rear == -1)
    {
        front = rear = 0;
        pri_que[rear] = data;
    }
    else
    {
        check(data);
        rear++;
    }
}

void dequeue()
{
    if (front == -1 || front > rear)
    {
        printf("\nQueue Underflow");
        return;
    }
    else
    {
        printf("\nDeleted element: %d", pri_que[front]);
        front++;
    }
}

void display_pqueue()
{
    if (front == -1 || front > rear)
    {
        printf("\nQueue is empty");
        return;
    }

    printf("\nPriority Queue elements: ");
    for (int i = front; i <= rear; i++)
    {
        printf("%d ", pri_que[i]);
    }
}

int main()
{
    int n, ch;

    while (1)
    {
        printf("\n1.Insert\n2.Delete\n3.Display\n4.Exit");
        printf("\nEnter your choice: ");
        scanf("%d", &ch);

        switch (ch)
        {
        case 1:
            printf("Enter value: ");
            scanf("%d", &n);
            insert_by_priority(n);
            break;

        case 2:
            dequeue();
            break;

        case 3:
            display_pqueue();
            break;

        case 4:
            exit(0);

        default:
            printf("\nInvalid choice");
        }
    }
}
```

