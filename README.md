#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#define MAXSZ 10
typedef struct database
{
    int roll;
    char name[50];
    int clas;
    char divi[2];
}database;
//--------------------------------
void add(database[],int *size);
void create(database[],int *size);
int search(database[],int size);
void modify(database[],int size);
void display(database student[],int size);
void deletes(database[],int *size);
//--------------------------------
int main()
{
    database student[MAXSZ];
    int ch,size=0,i=0,f;
    while(i!=1)
    {
        printf("Main Menu \n1) Create\n2) Display \n3) Add \n4) Search   \n5) Modify \n6)Delete \n7) Exit \n Enter choice: ");
        scanf("%d"&ch);
        
        switch(ch)
        {
            case 1:
                    printf("Enter Size:");
                    scanf("%d"&size);
                    create(student,&size);
                    break;
            case 2:
                    display(student,size);
                    break;
            case 3:
                    add(student,&size);
                    break;
            case 4:
                    f=search(student,size);
                    if(f==0)
                    printf("Student not found.\n");
                    break;
            case 5:
                    modify(student,size);
                    break;
            case 6:
                    deletes(student,&size);
                    break;
            case 7:
                    i=1;
                    break;
            default:
                    printf("ENTER NUMBER BETWEEN 1-7 ONLY.");
        }
    }
    return 0;
}
//--------------Create Function-------------------
void create(database student[],int *size)
{
    int i=0;
    if(*size<MAXSZ)
    {
        for(i=0;i<*size;)
        {
            add(student,&i);
        }
    }
    else
    {
        printf("\nCreation Failed!!\n");
        *size=0;
    }
}
//--------------Add Function-------------------
void add(database student[],int *size)
{
    if(*size<MAXSZ)
    {
        printf("Enter Name:");
        scanf("%c"&student[*size].name);
        printf("Enter Roll_No:");
        scanf("%d"&student[*size].roll);
        printf("Enter Class:");
        scanf("%d",&student[*size].clas);
        printf("Enter Division:");
        scanf("%c",&student[*size].divi);
        ++*size;
    }
    else
    {
        printf("NO MORE STUDENT CAN BE ACCOMODATED!!");
    }
}
