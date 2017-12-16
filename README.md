#include<iostream>
#include <cstdlib>

using namespace std;
string x,y;
double z,date,month,year,numberofstudents,b;
int choice,fid,delid;
class list{
 	private:
 		struct node{
			string firstName,lastName;   
 			int id,dob[3];
    	    double gpa;
			node *next;
		};
	public:
		node *head;
		list(){
			head=NULL;
		}
	~list(){
 		node *t;
 		t=head;
 		while(head!=NULL){
 			head=head->next;
 			delete t;
		}
	}

void insert(string x,string y,int z,double b,int date,int month,int year)
{
	
	node *ptr = new node;
 	ptr->firstName=x; // adding data
 	ptr->lastName=y;
 	ptr->id=z;
 	ptr->dob[0]=date;
 	ptr->dob[1]=month;
 	ptr->dob[2]=year;
	ptr->gpa=b;
	ptr->next = NULL; // setting it to NULL

	if (head == NULL)
	{
		head = ptr;
	}
	else
	{
		node *temp;
		temp = head;
		while(temp->next != NULL)
		{
			temp = temp->next;
			
		}
		temp ->next = ptr;
	}
}
void search()
{
	cout << "Please Enter Student ID: " << endl;
	cin >> fid;
	node *p=new node;
    p=head;
    while(p!=NULL)
	{
        if(p->id==fid)
		{
            cout << "DISPLAYING THE SEARCHED DATA"<< endl;
	        cout << "________________________________________________________________________________" << endl;
            cout <<  "Student's Name:"<<"\t" << p->firstName << " " << p->lastName << endl;
            cout <<  "Student's ID: "<< p->id<< endl;
            cout << "Student's CGPA: " << p->gpa << endl;
            cout << "Student's Date of Birth: ";  
           
            for(int l=0; l<3; l++)
			{
            	if (l == 2)
    			{
    			cout << p->dob[l] << endl;	
				}
				else
				{
					cout << p->dob[l];
					cout << "-";
				}
            }
	      
            return;
        }
	p=p->next;
    }
     cout << "INVALID ID ENTERED" << endl;
}

void del()
{
cout << "ENTER THE STUDENT ID FOR DELETION" << endl;
cin >> delid;

	node *nodePtr, *previousNode;

// If the list is empty, do nothing	
	if (!head)		
		return;
		
// Determine if the first node is the one.
	if (head->id == delid)	
		{
		nodePtr = head->next;		
		delete head;		
		head = nodePtr;	
		}
	else	
		{
		// Initialize nodePtr to head of list		
		nodePtr = head;
		
		
	// Skip all nodes whose value member is not equal to num.
	while (nodePtr != NULL && nodePtr->id != delid)		
		{
		previousNode = nodePtr;
		nodePtr = nodePtr->next;
		}		
	// Link the previous node to the node after		
	// nodePtr, then delete nodePtr.		
	previousNode->next = nodePtr->next;		
	delete nodePtr;
		}
		
}

 void display()
{

  node *t=head;
  int i=1;
    while(t!=NULL)
    {	cout << "________________________________________________________________________________" << endl;
    	cout << "DATA OF STUDENT: " << i <<endl;
    	cout << "Student's Name: " << t->firstName << " " << t->lastName << endl;
    	cout << "Student's ID: " << t->id << endl;
    	cout << "Students's Date of Birth: ";
    	for(int x=0; x<3; x++)
    	{
    		
    		if (x == 2)
    		{
    		cout << t->dob[x];	
			}
			else
			{
				cout << t->dob[x];
				cout << "-";
			}
		}
		cout << endl;
		cout << "Student's CGPA: " << t->gpa << endl;
		cout << "________________________________________________________________________________" << endl;

    	cout << endl;
    	t=t->next;
    	i++;
	}
}


};
//the menu is here

void menu(list &l)
{
	comehere:
	cout << "________________________________________________________________________________" << endl;
	cout << endl;
	cout <<  "                  PRESS 1 TO ADD RECORD OF A STUDENT          " << endl;
	cout <<  "                  PRESS 2 TO EDIT THE RECORD OF A STUDENT?    " << endl;
	cout <<  "                  PRESS 3 TO SEARCH THE RECORD OF A STUDENT   " << endl;
	cout <<  "                  PRESS 4 TO DELETE THE RECORD OF A STUDENT   " << endl;
	cout <<  "                  PRESS 5 TO DISPLAY THE RECORD OF A STUDENT  " << endl;
	cout << endl;
    cout << "________________________________________________________________________________ " << endl;



	cout <<endl;
	cout << "                     CHOOSE FROM MENU \nENTER YOUR OPTION : ";    cin >> choice;
	switch(choice)
	{
	case 1:
		cout << endl;
	cout <<"How many student's data you want to enter?" << endl;
	cin >> numberofstudents;
	cout << endl;
	system("CLS");
	for(int i=0; i<numberofstudents; i++)
	{   cout << endl;
		cout << "DATA ENTRY OF STUDENT "<< i+1 <<endl;
		cout << "Enter First Name:" << endl;
		cin >> x;
		cout << "Enter Last Name:" << endl;
		cin >> y;
		cout << endl;
		cout << "Enter ID:" << endl;
		cin >> z;
		cout << endl;
		cout << "Enter Date of Birth:" << endl;
		cout << "Day: " << endl;
		cin >> date;
		cout << "Month:" << endl;
		cin >> month;
		cout << "Year:" << endl;
		cin >> year;
		cout << endl;
		cout << "Enter CGPA:" << endl;
		cin >> b;
		cout << endl;

		l.insert(x,y,z,b,date,month,year); 
		system("CLS");
	}

	 goto comehere;
	 case 3:
     system("CLS");
	 l.search();
	  goto comehere;
    break;

    case 4:
	  system("CLS");
	  l.del();
	   goto comehere;
	  
    case 5:
    system("CLS");
    l.display();
    	goto comehere;


	}
}

int main(){
list c;
menu(c);

}
