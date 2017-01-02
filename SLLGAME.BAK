#include <iostream.h>
#include <stdlib.h>
#include <malloc.h>
#include <stdio.h>
#include <conio.h>
#include <process.h>
#include <string.h>
char passwd[7]="qwerty";

typedef struct sll      //sll refers to singly linked list the main structure of all the nodes
{
    char colour;
    struct sll *link;
}block;
block *head=NULL,*last;
int noofblock;
void intro();
void menu();
block *getblock();
void readblock(block *newblock);
void play();
void create();
void createlist(block **headptr);
void insertblock(block **headptr);
void display(block *headptr);
void checkblocksame();
void blaster(block *headptr1);
//////////////////////////////
void intro()
{
    clrscr();
    cout<<"\n\n\t\t\t\tBLOCK BUSTER\n";
    cout<<"\nINSTRUCTIONS ::\n";
    cout<<" * In this game you can insert a colour block in between a set of blocks \n";
    cout<<" * If you form a set of 3 same colour consecutive blocksthe 3 blocks vanishes\n";
    cout<<" * You will be given 3 chances to insert blocks.. finally the total number of blocks remaining is your score\n";
    cout<<" * Try getting a minimum score\n\n";
}
/////////////////////////////
void menu()
{
    char temp1;
    cout<<"\n\nPress 'a' to get into the administrator account\n\nPress 'p' to start playing the game\n\npress any other key to exit\n\n";
    flushall();
    cin>>temp1;
    switch(temp1)
    {
	case 'a':create();
		break;
	case 'p':play();
		break;
	default :exit(1);
    }

}
/////////////////////////////
void create()
{
    clrscr();
   // block *head=NULL;
    char temp3,temp2[7];
    cout<<"Enter you administrator password\n";
    flushall();
    cin>>temp2;
    if(strcmp(temp2,passwd)!=0)
    {
	cout<<"You have entered the wrong password";
	menu();
    }
    else
    {
	cout<<"Press 'c' to create the main colour block list\n";
	flushall();
	cin>>temp3;
	if(temp3=='c'||temp3=='C')
	createlist(&head);
    }
}
////////////////////////////
block* getblock()
{
    block *newblock;
    newblock=(block *)malloc(sizeof(block));
    return(newblock);
}
////////////////////////////
void readblock(block *newblock)
{
    cout<<"Enter the colour to be inserted i.e 'r' for red , 'b' for blue , 'g' for green\n ";
    cin>>newblock->colour;
    newblock->link=NULL;
}
////////////////////////////
void createlist(block **headptr)
{
    char temp3;
    //block *head=NULL,*last;
    block *newblock;
      a:newblock=getblock();
	readblock(newblock);
	if(head==NULL)
	{
	    head=newblock;
	    last=head;
	}
	else
	{
	    last->link=newblock;
	    last=last->link;

	}
    flushall();
    cout<<"If you want one more colour block press 'y' press any other key to exit to the main menu\t";
    cin>>temp3;
    if(temp3=='y'||temp3=='Y')
    goto a;
    else
    menu();
}
////////////////////////////
void insertblock(block *headptr)              //To add a new colour block inside the list
{

	int pos;
	//block *last;
	block *newblock;
	char tempcol;                           //temporary colour
	if(headptr==NULL)
	{
	    newblock=getblock();
	    readblock(newblock);
	    head=newblock;
	}
	else
	{
	    cout<<"Enter after which block you want to insert the colour block\n\n";
	    cout<<"Example: Entering '2' will insert the colour block between 2nd and 3rd block \n";
	    cin>>pos;
	    if(pos==0)
	    {
	     headptr=head;
	     newblock=getblock();
	     readblock(newblock);
	     newblock->link=headptr->link;
	     headptr->link=newblock;
	    }
	    else if(pos<0)
	    {
	     cout<<"Enter valid position\n";
	     play();
	    }
	    else
	    {
	    for(int temp6=0;temp6<pos-1;temp6++)
	    headptr=headptr->link;
	    newblock=getblock();
	    readblock(newblock);
	    newblock->link=headptr->link;
	    headptr->link=newblock;
	    //last->link=newblock;
	    }
	}

}
////////////////////////////
void checkblocksame(block *headptr)           //To check whether there are 3 same coloured consecutive blocks
{
	for(;headptr!=NULL;headptr=headptr->link)
	{       block *temp8;
		temp8=headptr;
		if(temp8->colour=='r')
		 {	temp8=temp8->link;
			if(temp8->colour=='r')
			 {	temp8=temp8->link;
				if(temp8->colour=='r')
					blaster(headptr);
			 }
		 }
		else if(temp8->colour=='b')
		 {	temp8=temp8->link;
			if(temp8->colour=='b')
			 {	temp8=temp8->link;
				if(temp8->colour=='b')
					blaster(headptr);
			 }
		 }
		 else if(temp8->colour=='g')
		 {	temp8=temp8->link;
			if(temp8->colour=='g')
			 {	temp8=temp8->link;
				if(temp8->colour=='g')
					blaster(headptr);
			 }
		 }

	}

}
////////////////////////////
void blaster(block *headptr1)
{       int counter=0;
	block *headptr2=head,*prevsame=head,*nextsame=head;
	block *a=NULL,*b=NULL,*c=NULL;
	a=headptr1;
	b=headptr1->link;
	c=headptr1->link->link;
	for(;headptr2!=headptr1;headptr2=headptr2->link)
	{
		counter++;
	}
	for(int temp10=1;temp10<counter;temp10++)
	{
		prevsame=prevsame->link;
	}
	for(temp10=1;temp10<=counter+3;temp10++)
	{
		nextsame=nextsame->link;
	}
		free(a);
		free(b);
		free(c);

	prevsame->link=nextsame;
}
////////////////////////////
void display(block *headptr)        //To display the contents of the list
{
     noofblock=0;
    if(headptr==NULL)
    {
	cout<<"\nList is empty\n";
    }
    else
    {
	cout<<"\n";
	for(;headptr!=NULL;headptr=headptr->link)
	{   noofblock++;
	    if(headptr->colour=='g'||headptr->colour=='G')

	    {
	    textcolor(GREEN);
	    cout<<"GREEN\t";
	    }
	    else if(headptr->colour=='r'||headptr->colour=='R')
	    {
	    textcolor(RED);
	    cout<<"RED\t";
	    }
	    else if(headptr->colour=='b'||headptr->colour=='B')
	    {
	    textcolor(BLUE);
	    cout<<"BLUE\t";
	    }
	}

    }
  textcolor(WHITE);
}
////////////////////////////
void play()
{
    clrscr();
    //block *head=NULL;
    int pos;
    char temp5;
    display(head);
    cout<<"You have only three turns\nTry to minimize the blocks\n\n";
    for(int temp4=0;temp4<3;temp4++)
    {
	insertblock(head);
	checkblocksame(head);
	display(head);

    }
    cout<<"\n\n\n\t\t\tYour score is "<<noofblock<<"\n\n";
    cout<<"press 'e' to exit\n";
    flushall();
    cin>>temp5;
    if(temp5=='e'||temp5=='E')
	exit(1);
    else
	exit(1);

}
/////////////////////////////
int main()
{
    intro();
    menu();

}
