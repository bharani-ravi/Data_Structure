
#include <stdio.h>
#include <stdlib.h>
struct node
{
    int coeff;
    int power;
    struct node *next;
}*head,*tail,*temp,*t;
struct node*polyadd(struct node *poly1,struct node *poly2);
struct node * createnode(int c ,int p)
{
    temp=(struct node *)malloc (sizeof(struct node));
    temp->coeff=c;
    temp->power=p;
    temp->next=NULL;
    return temp;
}
struct node *createpoly (int count ,int co[],int po[])
{
    int i;
    struct node *polylink=NULL,*last=NULL;
    for(i=0;i<count;i++)
    {
        t=createnode ( co[i],po[i]);
        if(polylink==NULL)
        {
            polylink=last=t;
        }
        else
        {
            last->next=temp;
            last=last->next;
        }
    }
    return (polylink);
}
void display(struct node *first)
{
    temp=first;
    printf("polynomial\n");
    while(temp!=NULL)
    {
        printf("%dx^%d\n",temp->coeff,temp->power);
        temp=temp->next;
    }
}

int main()
{
    int c1=5;
    int ac1[]={5,4,6,7,8};
    int ap1[]={6,3,2,1,0 };
    int c2=3;
    int ac2[]={13,14,16};
    int ap2[]={4,3,2};
    struct node *poly1,*poly2,*poly3=NULL;
    poly1=createpoly(c1,ac1,ap1);
    poly2=createpoly(c2,ac2,ap2);
    display(poly1);
    display(poly2);
    poly3=polyadd(poly1,poly2);
    display(poly3);
    return 0;
}
struct node*polyadd(struct node *poly1,struct node *poly2)
{
    struct node*p,*q,*res=NULL,*reslast=NULL;
    p=poly1;
    q=poly2;
    while(1)
    {
        if(p==NULL||q==NULL)
        {
            break;
        }
        if(p->power > q->power)
        {
            t=createnode(p->coeff,p->power);
            p=p->next;
        }
        else if(p->power <q->power)
        {
            t=createnode(q->coeff,q->power);
            q=q->next;
        }
        else
        {
            t=createnode(p->coeff+q->coeff ,q->power);
            p=p->next;
            q=q->next;
        }
        if(res==NULL)
        {
            res=reslast=t;
        }
        else
        {
            reslast->next=t;
            reslast=reslast->next;
        }
        
    }
    while(p!=NULL)
    {
        t=createnode(p->coeff,p->power);
        p=p->next;
        if(res==NULL)
        {
            res=reslast=t;
        }
        else
        {
            reslast->next=t;
            reslast=reslast->next;
        }
    }
    while(q!=NULL)
    {
        t=createnode(q->coeff,q->power);
        q=q->next;
        if(res==NULL)
        {
            res=reslast=t;
        }
        else
        {
            reslast->next=t;
            reslast=reslast->next;
        }
    }
    return (res);
}

Output:
polynomial
5x^6
4x^3
6x^2
7x^1
8x^0
polynomial
13x^4
14x^3
16x^2
polynomial
5x^6
13x^4
18x^3
22x^2
7x^1
8x^0
