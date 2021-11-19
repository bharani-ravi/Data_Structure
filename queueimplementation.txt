#include <stdio.h>
#include <string.h>
#define size 100
char stack[size];
char queue[size];
void push(char s);
char pop();
void enqueue(char s);
char dequeue();
int top=-1,front=0,rear=-1;
int main()
{
    char str[50];
    printf("enter the string to reverse :");
    scanf("%s",str);
    for(int i=0;i<strlen(str);i++)
    {
        enqueue(str[i]);
    }
    for(int i=0;i<strlen(str);i++)
    {
        push(dequeue());
    }
    for(int i=0;i<strlen(str);i++)
    {
        char v=pop();
        enqueue(v);
    }
    printf("the reversed string :");
    for(int i=0;i<strlen(str);i++)
    {
        char v= dequeue();
        printf("%c",v);
    }
    return 0;
}
void push(char s)
{
    top++;
    stack[top]=s;
}
void enqueue(char s)
{
    rear++;
    queue[rear]= s;
}
char dequeue()
{
    char d=queue[front];
    front++;
    return(d);
}
char pop()
{
    char d=stack[top];
    top--;
    return(d);
}


Output:

enter the string to reverse :github
the reversed string :buhtig
