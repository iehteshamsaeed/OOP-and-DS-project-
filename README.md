#include<iostream>
#include <cstdlib>

using namespace std;
 string x,y;
 int z,date,month,year,b,numberofstudents,choice,fid;

 struct node {

 	string uname,fname;
 	int id,dob[3];
   float gpa;

   node *next;

 };

 class list{
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

 void insert( string x,string y,int z,int b,int date,int month,int year)
 {

 	node *ptr= new node;

 	ptr->uname=x; // adding data
 	ptr->fname=y;
 	ptr->id=z;
 	ptr->dob[0]=date;
 	ptr->dob[1]=month;
 	ptr->dob[2]=year;

 	ptr->gpa=b;
 ptr->next = NULL; // setting it to NULL

  if (head==NULL)
{
  head =ptr;
}
else
 {
node *temp;
temp=head;
while(temp->next!=NULL){
temp = temp->next;
}
   temp ->next =ptr;
}

 }
void search(){
cout << "enter the ID of the student " << endl;
cin >> fid;
node *p=new node;
    p=head;
    while(p!=NULL){
        if(p->id==fid){
            cout << " DISPLAYING YOUR DATA "<< endl;
            cout <<   p->uname  << endl;
            cout <<   p->fname  <<endl;
            cout <<   p->id     << endl;
            for(int l=0; l<3; l++){
                cout <<   p->dob[l]   << endl;
            }


            return;
        }

        p=p->next;
    }
     cout << "invalid" << endl;
     




}

 void display()
{

  node *t=head;
    while(t!=NULL)
    {
        cout << "\t Student name:\t" << endl;
       cout<<t->uname<<"\t"<< endl;
       cout<<endl;
       cout << " \t Father name:\t " << endl;
      cout<<t->fname<<"\t" << endl;
      cout<<endl;
      cout << "\t ID:\t" << endl;
      cout<<t->id<<"\t" << endl;
      cout<<endl;
     cout<<" \t Date of birth:-"<<endl;
	cout<<"\t Date:\t"<< date<<endl;
	cout<<" \t Month:\t"<< month <<endl;
	cout<<"\t Year:\t"<< year <<endl;
	cout<<endl;
	cout << "\t Your Gpa:\t" << endl;
      cout<<t->gpa<<"\t" << endl;
      cout << endl;
      cout << endl;
      t=t->next;

    }

}


};
//the menu is here

void menu(list &l){
    comehere:
cout << "Press 1 for add record of student" << endl;
cout << "Press 2 for editing record of student" << endl;
cout << "Press 3 for searching record of student " << endl;
cout << "Press 4 for removing record of student" << endl;

cout << "**********" << endl;
cout <<endl;
cout << "Enter Choice " << endl;
cin >> choice;
	switch(choice)
	{
	case 1:
	cout << " \t How many students data you want to enter " << endl;
	cout << endl;
	cin >> numberofstudents;
	cout << endl;
	for(int i=0; i<numberofstudents; i++){

	cout << "\t Enter name of student ::"<< i << endl;
	cout << endl;
	cin >> x;
	cout << endl;
	cout << "\t Enter father name of student ::"<<i << endl;
	cout << endl;
	cin >> y;
	cout << endl;
	cout << "\t Enter Id of student ::" << i << endl;
	cout << endl;
	cin >> z;
	cout << endl;
	cout << "\t Enter Date of student ::" << i << endl;
	cout << endl;
	cin >> date;
	cout << endl;
	cout << "\t Enter Month of student ::" << i <<endl;
	cout << endl;
	cin >> month;
	cout << endl;
	cout << "\t Enter Year of student ::" << i << endl;
	cout << endl;
	cin >> year;
	cout << endl;

	cout << "\t Enter Gpa of student ::" << i << endl;
	cout << endl;
	cin >> b;
	cout << endl;

l.insert(x,y,z,b,date,month,year);

	 }

	 goto comehere;

	 case 3:


	 l.search();
    break;




	}
}

int main(){
list c;
menu(c);
//system("CLS");
//c.display();

}
