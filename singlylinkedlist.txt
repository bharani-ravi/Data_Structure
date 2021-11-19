#include<stdio.h>
#include<stdlib.h>

struct node
{
    int data;
    struct node *next;
};

struct node *head,*ptr,*temp;
void create_node();
void insert_begin();
void insert_middle_before_value();
void insert_middle_after_value();
void insert_last();
void delete_first();
void delete_middle_before_value();
void delete_middle_after_value();
void delete_last();
void print_all(struct node *);
int main()
{
    int choice;
    while (1)
    {
    
    printf("\n1.Create Node\n2.Insert Beginning \n3.Insert Middle Before Value\n4.Insert Middle After Value\n5.Insert Last\n6.Delete First\n7.Delete Middle before Value\n8.Delete Middle After Value\n9.Delete Last \nEnter your Choice :");
    scanf("%d",&choice);

    switch (choice)
    {
    case 1:
        create_node();
        break;
    
    case 2:
        insert_begin();
        break;
    case 3:
        insert_middle_before_value();
        break;
    
    case 4:
        insert_middle_after_value();
        break;
    
    case 5:
        insert_last();
        break;
    
    case 6:
        delete_first();
        break;
    
    case 7:
        delete_middle_before_value();
        break;
    
    case 8:
        delete_middle_after_value();
        break;
    
    case 9:
        delete_last();
        break;
    default:
        printf("Invalid Option !");
        exit(1);
        break;
        
    }
    }
}

void print_all(struct node *temp)
{
    while (temp!=NULL)
    {
        printf("\nData  - - - > > > %d",temp->data);
        temp=temp->next;
    }
    
}
void create_node()
{
    head = (struct node *)malloc(sizeof(struct node));
    if(head==NULL)
    {
        printf("Memory Not Allocated !");
        exit(1);
    }
    else
    {
        printf("Enter the Number :");
        scanf("%d",&head->data);
        head->next=NULL;
    }
}
void insert_begin()
{
    ptr= (struct node *)malloc(sizeof(struct node));
    if(ptr==NULL)
    {
        printf("Memory Not Allocated !");
        exit(1);
    }
    else
    {
        printf("Enter the Number to add at Beginning :");
        scanf("%d",&ptr->data);
        ptr->next=NULL;
        
    
        ptr->next=head;
        head=ptr;

        print_all(head);
    }
}
void insert_middle_before_value()
{
    int val;
    ptr=(struct node *)malloc(sizeof(struct node));
    if(ptr==NULL)
    {
        printf("Memory Not Allocated !");
        exit(1);
    }
    printf("Enter the Value :");
    scanf("%d",&val);
    printf("Enter the Number to be Added Middle :");
    scanf("%d",&ptr->data);
    ptr->next=NULL;
    temp=head;
    while (temp->next->data!=val){
        temp=temp->next;
        if(temp==NULL)
        {
            printf("Number not found !");
            exit(1);
        }

    }
    ptr->next=temp->next;
    temp->next=ptr;
    
    print_all(head);

}
void insert_middle_after_value()
{
    int val;
    ptr=(struct node *)malloc(sizeof(struct node));
    if(ptr==NULL)
    {
        printf("Memory Not Allocated !");
        exit(1);
    }
    printf("Enter the Value :");
    scanf("%d",&val);
    printf("Enter the Number to be Added Middle :");
    scanf("%d",&ptr->data);
    ptr->next=NULL;
    temp=head;
    while (temp->data!=val){
        temp=temp->next;
        if(temp==NULL)
        {
            printf("Number not found !");
            exit(1);
        }
    }    
    ptr->next=temp->next;
    temp->next=ptr;
    
    print_all(head);
}
void insert_last()
{
    ptr=(struct node *)malloc(sizeof(struct node));
    if(ptr==NULL)
    {
        printf("Memory Not Allocated !");
        exit(1);
    }
    printf("\nEnter the Number to be added last :");
    scanf("%d",&ptr->data);
    ptr->next=NULL;
    temp=head;
    while (temp->next!=NULL)
    {
        temp=temp->next;
        
    }
    temp->next=ptr;

    print_all(head);
}
void delete_first()
{
    if(head==NULL)
    {
        printf("List is Empty !");
    }
    else
    {
        temp=head;
        head=head->next;
        printf("%d Data Removed !",temp->data);
        free(temp);
    }
    print_all(head);
}
void delete_middle_before_value()
{
    int val;
    struct node *prev;
    if(head==NULL)
        printf("List is Empty !");
    else
    {
        printf("Enter the Value ,that before element to be removed:");
        scanf("%d",&val);
        prev=head;
        temp=head;

        while (temp->next->data!=val)
        {
            if(temp->next==NULL)
                printf("The Value you entered is not found !");
            prev=temp;
            temp=temp->next;
        }
        prev->next=temp->next;
        free(temp);
        temp->next=NULL;
    }

    print_all(head);
    
    
}
void delete_middle_after_value()
{
    int val;
    struct node *prev;
    if(head==NULL)
        printf("List is Empty !");
    else
    {
        printf("Enter the Value ,that after element to be removed:");
        scanf("%d",&val);
        prev=head;
        temp=head;

        while (temp->data!=val)
        {
            prev=temp;
            temp=temp->next;
            if(temp->next==NULL)
                printf("The Value you entered is not found !");
        }
        prev->next=temp->next;
        free(temp);
        temp->next=NULL;
    }
    print_all(head);
}
void delete_last()
{
    struct node *prev = head;
    temp = head;
    if(head==NULL)
    {
    	printf("List is Empty ");
	}
	else if(head->next==NULL)
	{
		free(head);
		printf("Ele");
	}
	else
	{
	
    while (temp->next!=NULL)
    {
        prev = temp;
        temp = temp->next;
        if(temp == NULL)
            break;
    }
    
    prev->next = NULL;
    free(temp);

    print_all(head);
}
}
/*
output:
1.Create Node
2.Insert Beginning 
3.Insert Middle Before Value
4.Insert Middle After Value
5.Insert Last
6.Delete First
7.Delete Middle before Value
8.Delete Middle After Value
9.Delete Last 
Enter your Choice :1
Enter the Number :10 

1.Create Node
2.Insert Beginning 
3.Insert Middle Before Value
4.Insert Middle After Value
5.Insert Last
6.Delete First
7.Delete Middle before Value
8.Delete Middle After Value
9.Delete Last 
Enter your Choice :5

Enter the Number to be added last :80

Data  - - - > > > 10
Data  - - - > > > 80
1.Create Node
2.Insert Beginning 
3.Insert Middle Before Value
4.Insert Middle After Value
5.Insert Last
6.Delete First
7.Delete Middle before Value
8.Delete Middle After Value
9.Delete Last 
Enter your Choice :3
Enter the Value :80
Enter the Number to be Added Middle :50

Data  - - - > > > 10
Data  - - - > > > 50
Data  - - - > > > 80
1.Create Node
2.Insert Beginning 
3.Insert Middle Before Value
4.Insert Middle After Value
5.Insert Last
6.Delete First
7.Delete Middle before Value
8.Delete Middle After Value
9.Delete Last 
Enter your Choice :8
Enter the Value ,that after element to be removed:10

Data  - - - > > > 0
1.Create Node
2.Insert Beginning 
3.Insert Middle Before Value
4.Insert Middle After Value
5.Insert Last
6.Delete First
7.Delete Middle before Value
8.Delete Middle After Value
9.Delete Last 
Enter your Choice :10
Invalid Option !
*/