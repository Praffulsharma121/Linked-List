# Linked-List
//All Methods of Linked list such as Insert a Node at head, Insert a Node at specific location, Delete a Node, Reverse a Linked list, Get a Node value - in C language 

#include<stdio.h>
#include<stdlib.h>
#include<assert.h>
#include<math.h>

struct Node
{
    int data;
    struct Node* next;
};

struct Node* head;

void Insert(int x)
{
    struct Node* temp = (struct Node*) malloc(sizeof(struct Node));
    temp->data = x;
    temp->next = NULL;

    if(head != NULL)
        temp->next = head;
    head = temp;
}

void Print()
{
    struct Node* temp = head;
    printf("The Linked list is: \n");
    while(temp != NULL)
    {
        printf("%d\n", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

void InsertNode(int pos_cha, int newdata)
{
    struct Node* temp = (struct Node* )malloc(sizeof(struct Node* ));
    temp->data=newdata;    

    struct Node* temp2=head;
    
    if(pos_cha==1)
    {
        temp->next=temp2;
        head=temp;
        return ;
    }
        
    for(int i=1;i<pos_cha;i++)
    {
        temp2=temp2->next;
    }

    temp->next=temp2->next;
    temp2->next=temp;
    return;
}

void PrintNew()
{
    struct Node* temp = head;
    printf("The New Linked list is: \n");
    while(temp != NULL)
    {
        printf("%d\n", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

void Delete(int delete)
{
    struct Node* temp = head;
    if(delete == 1)
    {
        head = temp->next;
        free(temp);
        return;
    }
    for(int i=0;i<delete-2;++i)
        temp = temp->next;
    {
        struct Node* temp2 = temp->next;
        temp->next = temp2->next;
        free(temp2);
    }
}

void Reverse()
{
    struct Node* current, *prev, *next;

    current = head;
    prev = NULL;
    while(current != NULL)
    {
        next = current->next;
        current->next = prev;

        prev = current;
        current = next;
    }
    head = prev;
    return;
}

void PrintReverse()
{
    struct Node* temp = head;
    printf("The Reversed Linked list is: \n");
    while(temp != NULL)
    {
        printf("%d\n", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int GetNodeValue(int x, int y)
{
    struct Node* current = head;
    int count = 0;

    while(current != NULL)
    {
        if(count == y)
        {
            return(current->data);
        }
        count ++;
    current = current->next;

    }
    
    assert(0);
}

int main()
{
    head = NULL;
    int lenght, data, pos_cha, newdata, delete, position;
    char ansI, ansD, ansR, ansG;

    printf("Enter the lenght of the Linked list: \n");
    scanf("%d", &lenght);

    for(int i=0;i<lenght;++i)
        {
            printf("Enter the value: \n");
            scanf("%d", &data);
            Insert(data);
            Print();
        }

    printf("Do you want to Insert a Node Press y for yes and n for no: \n"); 
    scanf("%s", &ansI); 
    if(ansI == 'y')
    {
        printf("Enter the position:  \n");
        scanf("%d", &pos_cha);
        printf("Enter the new value: \n");
        scanf("%d", &newdata);
        InsertNode(pos_cha, newdata);
        PrintNew();
    }
    else if(ansI == 'n')
    {  
        printf("No ok\n");
        Print();
    }
    else
        printf("Error.\n");

    printf("Do you want to Delete a Node Press y for yes and n for no: \n");
    scanf("%s", &ansD);

    if(ansD == 'y')
    {
        printf("Which node you want to delete: \n");
        scanf("%d", &delete);
        Delete(delete);
        PrintNew();
    }
    else if(ansD == 'n')
    {
        printf("No ok\n");
        Print();
    }
    else
        printf("Error.\n");

    printf("Do you want to Reverse the Linked list Press y for yes and n for no: \n");
    scanf("%s", &ansR);

    if(ansR == 'y')
    {
        Reverse();
        PrintReverse();
    }
    else if(ansR == 'n')
    {
        printf("NO ok.\n");
        Print();
    }
    else 
        printf("Error.\n");

    printf("Do want to know a Node value Press y for yes and n for no: \n");
    scanf("%s", &ansG);

    if(ansG == 'y')
    {
        printf("Enter the Position: \n");
        scanf("%d", &position);
        printf("The value at Node %d is -:a %d \n", position, GetNodeValue(data, position));
       
    }

    else if(ansG == 'n')
    {
        printf("No ok\n");
        PrintReverse();
    }
    else
        printf("Error. \n");
        
    return 0;
}
