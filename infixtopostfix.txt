#include <stdio.h>
#include <ctype.h>
#define SIZE 10            
char stack[SIZE];
int top=-1;
 
void push(char chr)
{  
    top++;
    stack[top]=chr;
}
 
char pop()
{                      
    return(stack[top--]);
    top--;
}
 
int prior(char sym)
{                
   
if(sym=='^')
{
return(3);
}
else if(sym=='*' || sym=='/')
{
return(2);
}
else if(sym=='+' || sym=='-')        
{
return(1);
}
else
{
return(0);
}
}

void main()
{                        
    char infix[50],postfix[50],ch,elem;
    int i=0,k=0;
    printf("Enter Infix Expression : ");
    scanf("%s",infix);
    while( (ch=infix[i++]) != '\0')
    {
        if( ch == '(') push(ch);
        else
        {
            if(isalnum(ch))
            postfix[k++]=ch;
            else
            {
                if( ch == ')')
                {
                    while( stack[top] != '(')
                    {
                        postfix[k++]=pop();
                    }
                    elem=pop();
                }
                else
                {      
                    while( prior(stack[top]) >= prior(ch) )
                        postfix[k++]=pop();
                    push(ch);
                }
            }
        }
    }
    while( top!=-1)    
        postfix[k++]=pop();
    postfix[k]='\0';        
    printf("\nPostfix Expression =  %s\n",postfix);
}

Output:
Enter Infix Expression : (a*b)+c-d

Postfix Expression =  ab*c+d-


