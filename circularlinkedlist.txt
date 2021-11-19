#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
struct node
{
    int data;
    struct node *next;
}*head,*tail,*tail,*temp,*t,*prev;
void createnode();
void createlink(int n);
void traverse();
void insertbeg();
void insertmid();
void insertend();
void deletebeg();
void deletemid();
void deleteend();
int main()
{
    int a,b;
    while(1)
    {
        printf("1.Create link\n2.Insert beg\n3.Insert mid\n4.Insert end\n5.Delete beg\n6.Delete mid\n7.Delete end\n8.Exit\n");
        scanf("%d",&a);
        switch(a)
        {
            case 1:
            {
                printf("Enter no. of nodes in list:");
                scanf("%d",&b);
                createlink(b);
                traverse();
                break;
            }
            case 2:
            {
                insertbeg();
                break;
            }
            case 3:
            {
                insertmid();
                break;
            }
            case 4:
            {
                insertend();
                break;
            }
            case 5:
            {
                deletebeg();
                break;
            }
            case 6:
            {
                deletemid();
                break;
            }
            case 7:
            {
                deleteend();
                break;
            }
            case 8:
            {
                exit(0);
            }
        }
    }    
    return(0);
}
void createnode()
{
    temp=(struct node*)malloc(sizeof(struct node));
    printf("Enter data: ");
    scanf("%d",&temp->data);
    temp->next=NULL;
}
void createlink(int n)
{
    int i;
    for(i=0;i<n;i++)
    {
        createnode();
        if(head==NULL)
        {
            head=temp;
            tail=head;
        }
        else
        {
            temp->next=head;
            tail->next=temp;
            tail=tail->next;

        }
    }
}
void traverse()
{
    temp=head;
    while(temp->next!=head)
    {
        printf("%d->",temp->data);
        temp=temp->next;
    }
    printf("%d",temp->data);
    printf("\n");
}
void insertbeg()
{
    createnode();
    if(head==NULL)
    {
        head=temp;
        tail=head;
    }
    else
    {
        tail->next=temp;
        temp->next=head;
        head=temp;
    }
    traverse();
}
void insertmid()
{
    int x;
    printf("Enter where to insert:");
    scanf("%d",&x);
    t=head;
    while(t->data!=x)
    {
        t=t->next;
    }
    if(t->data==x)
    {
        createnode();
        temp->next=t->next;
        t->next=temp;
        traverse();
    }
}
void insertend()
{
    createnode();
    if(head==NULL)
    {
        head=temp;
        tail=head;
    }
    else
    {
        tail->next=temp;
        tail=tail->next;
        tail->next=head;
    }
    traverse();
}
void deletebeg()
{
    if(head==NULL)
    {
        printf("no linked list found ");
    }
    else if(head->next==NULL)
    {
        free(head);
    }
    else
    {
        temp=head;
        head=head->next;
        tail->next=head;
        free(temp);
    }
    traverse();
}
void deleteend()
{
    temp=head;
    if(temp==NULL)
    {
        printf("there is no linked list");
    }
    else
    {
        while(temp->next!=head)
        {
            t=temp;
            temp=temp->next;
        }
        t->next=head;
        free(temp);
    }
    traverse();
}
void deletemid()
{
    int a;
    printf("enter data to delete");
    scanf("%d",&a);
    temp=head;
    while(temp->data!=a)
    {
        t=temp;
        temp=temp->next;
    }
    t->next=temp->next;
    free(temp);
    traverse();
}

Output:
1.Create link
2.Insert beg
3.Insert mid
4.Insert end
5.Delete beg
6.Delete mid
7.Delete end
8.Exit
1
Enter no. of nodes in list:5
Enter data: 1
Enter data: 2
Enter data: 3
Enter data: 4
Enter data: 5
1->2->3->4->5
1.Create link
2.Insert beg
3.Insert mid
4.Insert end
5.Delete beg
6.Delete mid
7.Delete end
8.Exit
3
Enter where to insert:3
Enter data: 8
1->2->3->8->4->5
1.Create link
2.Insert beg
3.Insert mid
4.Insert end
5.Delete beg
6.Delete mid
7.Delete end
8.Exit
7
1->2->3->8->4
1.Create link
2.Insert beg
3.Insert mid
4.Insert end
5.Delete beg
6.Delete mid
7.Delete end
8.Exit
8
