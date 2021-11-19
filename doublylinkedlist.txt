#include<stdio.h>
#include<stdlib.h>

struct node
{
    int data;
    struct node *prev;
    struct node *next;
};

struct node *head,*temp,*ptr,*prev;

void insert_first();
void insert_last();
void insert_middle();
void delete_first();
void delete_last();
void delete_middle();
void print_all(struct node *);
void reverse();

int main()
{
    int choice;
    char ch;

    do
    {
        printf("\n1.Insert First \n2.Insert Last \n3.Insert Middle\n4.Delete First\n5.Delete Last\n6.Delete Middle\n7.Reverse\nEnter your Choice :");
        scanf("%d",&choice);

        switch (choice)
        {
        case 1:
            insert_first();
            break;
        case 2:
            insert_last();
            break;
        
        case 3:
            insert_middle();
            break;

        case 4:
            delete_first();
            break;

        case 5:
            delete_last();
            break;
        
        case 6:
            delete_middle();
            break;

        case 7:
            reverse();
            break;
        default:
            printf("\nInvalid Choice !");
            break;
        }

        printf("\nDo you Want to Continue (y/n)");
        scanf("\n%c",&ch);
    } while (ch=='y');
    
}

void print_all(struct node *t)
{
    while (t!=NULL)
    {
        printf("Data - - - > > > %d\n",t->data);
        t=t->next;
    }
       
}
void insert_first()
{

    ptr=(struct node *)malloc(sizeof(struct node));
    printf("Enter the Data To be Added First :");
    scanf("%d",&ptr->data);

    if(head==NULL)
    {
        head=ptr;
        head->prev=NULL;
    }
    else
    {
        ptr->next=head;
        head->prev=ptr;
        head=ptr;
    }
    print_all(head);

}

void insert_last()
{
    ptr=(struct node *)malloc(sizeof(struct node));
    printf("Enter the Data to be Added Last :");
    scanf("%d",&ptr->data);

    if(head==NULL)
    {
        head=ptr;
        head->prev=NULL;
    }
    else
    {
        temp=head;
        while (temp->next!=NULL)
        {
            temp=temp->next;
        }
        ptr->next=NULL;
        temp->next=ptr;
        ptr->prev=temp;
		
        print_all(head);
    }
}

void insert_middle()
{
    int val;
    ptr=(struct node*)malloc(sizeof(struct node));
    printf("\nEnter the Value of Previous Element :");
    scanf("%d",&val);
    printf("Enter the Data :");
    scanf("%d",&ptr->data);
    temp=head;
    if(head==NULL)
    {
    	head=ptr;
	}
	else
	{
    while (temp->data!=val)
    {
        temp=temp->next;
        if(temp==NULL)
        {
        	printf("Data not found");
        	return;
		}
    }
	}
    ptr->next=temp->next;
    ptr->prev=temp;
    temp->next->prev=ptr;
    temp->next=ptr;
    
    print_all(head);
    
}

void delete_first()
{
    if(head==NULL)
    {
        printf("List is Empty");
        return;
    }
    else
    {
        head=head->next;
        head->prev=NULL;
    }
    print_all(head);
}

void delete_middle()
{
    int val;
    printf("Enter the Number you want to delete :");
    scanf("%d",&val);
    
    temp=head;
    prev=head;
    
    if(head==NULL)
    {
        printf("Listis Empty");
        return;
    }
    else{    
    while(temp->data!=val)
    {
        prev=temp;
        temp=temp->next;
    }
    }
    
    if(temp==head)
    {
        head=head->next;
        head->prev=NULL;
    }
    else
    {
        prev->next = temp ->next;
        temp->next->prev=prev;
        free(temp);
    }
    
    print_all(head);

}

void delete_last()
{
    prev=head;
    temp=head;
    
    if(head==NULL)
    {
        printf("List is Empty !");
        return;
    }
    else
    {
    while(temp->next!=NULL)
    {
        prev=temp;
        temp=temp->next;
    }
    prev->next=NULL;
    
    free(temp);
    
    print_all(head);
}
}

void reverse()
{
    temp = head;
    while (temp->next!=NULL)
    {
        temp=temp->next;
    }

    do
    {
        printf("Data   = = = > > %d\n",temp->data);
        temp=temp->prev;
    }while(temp!=NULL);

    
}


Output:
1.Insert First 
2.Insert Last 
3.Insert Middle
4.Delete First
5.Delete Last
6.Delete Middle
7.Reverse
Enter your Choice :1
Enter the Data To be Added First :1
Data - - - > > > 1

Do you Want to Continue (y/n)y

1.Insert First 
2.Insert Last 
3.Insert Middle
4.Delete First
5.Delete Last
6.Delete Middle
7.Reverse
Enter your Choice :2
Enter the Data to be Added Last :5
Data - - - > > > 1
Data - - - > > > 5

Do you Want to Continue (y/n)y

1.Insert First 
2.Insert Last 
3.Insert Middle
4.Delete First
5.Delete Last
6.Delete Middle
7.Reverse
Enter your Choice :3

Enter the Value of Previous Element :1
Enter the Data :4
Data - - - > > > 1
Data - - - > > > 4
Data - - - > > > 5

Do you Want to Continue (y/n)y

1.Insert First 
2.Insert Last 
3.Insert Middle
4.Delete First
5.Delete Last
6.Delete Middle
7.Reverse
Enter your Choice :5
Data - - - > > > 1
Data - - - > > > 4

Do you Want to Continue (y/n)n


