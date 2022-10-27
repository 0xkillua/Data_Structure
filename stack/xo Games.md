
## Solution c++
```c++
#include<bits/stdc++.h>
#include<windows.h>
#define max_size 30
using namespace std;
char Games[3][3];
/*-------------------------------------------------stack class---------------------------------------------------*/
class stac {
private:
	int items[max_size];
	int top;
public:
	stac() { top = -1; }

	void push(int element);
	int pop();
	bool is_empty();
	bool is_full();
	int peek() { return items[top]; }/*-------------return top of stack------------------------ */
	void print_all_elements();
};
/* ------------------------------------Push Function--------------------------------------*/
void stac::push(int element) {
	if (is_full())
	{
		cout << "Stack is overflow";
		return;
	} top++;
	items[top] = element;
}
/*-----------------------------------------------Pop Function-------------------------------------------------------*/
int stac::pop()
{
	if (is_empty())
	{
		cout << "Stack is underflow";
		return -1;
	}
	int element = items[top];
	top--;
	return element;
}
/* ----------------------------------------------------Is_empty Function---------------------------------------------*/
bool stac::is_empty() {
	if (top == -1) return true;
	return false;
}
/*-----------------------------------------------Is_full Function----------------------------------*/
bool stac::is_full() {
	if (top == max_size - 1) return 1;
	return 0;
}
/*=---------------------------------------------------------print element------------------------------------------- */
void stac::print_all_elements()
{
	for (int i = 0; i < top - 1; i++)
		cout << items[i] << " ";
}

/*-----------------------------------------------check winner -----------------------------------------------------------------*/

bool check() /* check who is winner */
{
	if (((Games[0][0] == 'X' && Games[0][1] == 'X' && Games[0][2] == 'X')) || ((Games[1][0] == 'X' && Games[1][1] == 'X' && Games[1][2] == 'X')) || ((Games[2][0] == 'X' && Games[2][1] == 'X' && Games[2][2] == 'X')) ||
		((Games[0][0] == 'X' && Games[1][0] == 'X' && Games[2][0] == 'X')) || ((Games[0][1] == 'X' && Games[1][1] == 'X' && Games[2][1] == 'X')) || ((Games[0][2] == 'X' && Games[1][2] == 'X' && Games[2][2] == 'X')) ||
		((Games[0][0] == 'O' && Games[0][1] == 'O' && Games[0][2] == 'O')) || ((Games[1][0] == 'O' && Games[1][1] == 'O' && Games[1][2] == 'O')) || ((Games[2][0] == 'O' && Games[2][1] == 'O' && Games[2][2] == 'O')) ||
		((Games[0][0] == 'O' && Games[1][0] == 'O' && Games[2][0] == 'O')) || ((Games[0][1] == 'O' && Games[1][1] == 'O' && Games[2][1] == 'O')) || ((Games[0][2] == 'O' && Games[1][2] == 'O' && Games[2][2] == 'O')) ||
		((Games[0][0] == 'X' && Games[1][1] == 'X' && Games[2][2] == 'X')) || ((Games[0][2] == 'X' && Games[1][1] == 'X' && Games[2][0] == 'X')) ||
		((Games[0][0] == 'O' && Games[1][1] == 'O' && Games[2][2] == 'O')) || ((Games[0][2] == 'X' && Games[1][1] == 'X' && Games[2][0] == 'X')))
	{
		return 1;
	}
	return 0;
}
/*-------------------------------------------------------------------------------------------------------------------------*/
void Drow()
{
	system("cls");

	for (int row = 0; row < 3; row++)
	{
		cout << "| ";
		for (int colum = 0; colum < 3; colum++)
		{
			if (Games[row][colum] == 'X' || Games[row][colum] == 'O')
			{
				cout << Games[row][colum] << " | ";
			}
			else
			{
				cout << "-" << " | ";
			}

		}
		cout << endl;
	}
	if (check())
	{
		cout << "congratlation , you win" << endl;
	}


}
/*-----------------------------------------------------main---------------------------------------------------------------------------*/
int main()
{

	stac n1, n2;
	int row, colom, colom1, row1, colom2, row2;
	string name1, name2;
	int choice, start, player;
	cout << "Enter name the first  player : \t";
	cin >> name1;
	cout << "Enter name the second player : \t";
	cin >> name2;
	cout << "player one " << name1 << " will play with 'x' character and player two "
		<< name2 << "  will play with 'o'character " << endl;
	cout << "-----------------------------------------------------------------------------" << endl;
	cout << "Which player will start  1 - player one ( " << name1 << " )       2 - player two ( " << name2 << " ) : " << endl;
	cin >> player;
	while (!(check())) /*----------------continos play  while -----------------------------------------------*/
	{         
		switch (player)
		{                
		  case 1: {           //--------------------------------check who do you want first play---------------------------            
			start = 1;                   
			while (start == 1)           
			{
				cout << name1 << " pleas enter 1- cell posetion 2-undo 3-redo : ";
				cin >> choice;       
				switch (choice) {      
				case 1: {     //--------------replace--------------------------------------------
					cout << "please enter row and col to put  " << name1 << " : ";
					cin >> row >> colom;    
					if ((row == 0 || row == 1 || row == 2) && (colom == 0 || colom == 1 || colom == 2))    
					{
						if (Games[row][colom] == 'X' || Games[row][colom] == 'O')             
						{
							cout << "Invalid position" << endl;
							start = 1;
						}
						else
						{
							n1.push(row);                 
							n1.push(colom);                
							Games[row][colom] = 'X';
							start = 0;
						}
					}
					else {
						cout << "Invalid position \n";
						start = 1;
					}
					break;        
				}
				case 2: {              //--------------------------undo----------------
					if (n1.is_empty())  
					{
						cout << "There is no movements to undo yet" << endl;
						start = n1.pop();
					}
					else
					{
						colom1 = n1.pop();          
						row1 = n1.pop();              
						Games[row1][colom1] = '-';
						start = 1;
						Drow();          
					}
					break;	           
				}
				case 3: {       /*----------------------------redo-------------------------*/       
					if (!((row1 == 0 || row1 == 1 || row1 == 2) && (colom1 == 0 || colom1 == 1 || colom1 == 2)))                
					{
						start = n1.pop();
					}
					else
					{
						if (Games[row1][colom1] == 'X' || Games[row1][colom1] == 'O')            
						{
							cout << "There is no movements to redo yet" << endl;
							start = 1;
						}
						else
						{
							n1.push(row1);                                   
							n1.push(colom1);                         
							Games[row1][colom1] = 'X';                   
							start = 1;
							Drow();               
						}
					}
					break;                         
				}
				default: {                  
					cout << "invalid input" << endl;
					start = 1; }

				}
			}
			Drow();            
			if (check())      
			{
				system("pause");
				return 0;
			}
			player = 2;
			break;
		  }
			  /*------------------------------------------------------play two-------------------------------*/
		  case 2: {                     
			start = 1;                   
			while (start == 1)          
			{
				cout << name2 << " : enter 1-position 2-undo 3-redo : ";
				cin >> choice;                            
				switch (choice)                             
				{
				case 1: {                                  
					cout << "enter position " << name2 << " : ";
					cin >> row >> colom;                      
					if ((row == 0 || row == 1 || row == 2) && (colom == 0 || colom == 1 || colom == 2))      
					{
						if (Games[row][colom] == 'X' || Games[row][colom] == 'O')                
						{
							cout << "Invalid position" << endl;
							start= 1;
						}
						else
						{
							n2.push(row);                       
							n2.push(colom);                   
							Games[row][colom] = 'O';
							start = 0;
						}
					}
					else {
						cout << "error,try again" << endl;
						start = 1;
					}
					break;                       
				}
				case 2: {                  
					if (n2.is_empty())        
					{
						start = n2.pop();
					}
					else
					{
						colom2 = n2.pop();                  
						row2 = n2.pop();                      
						Games[row2][colom2] = '-';
						start = 1;
						Drow();
					}
					break;                               
				}
				case 3: {                                        
					if (!((row2 == 0 || row2 == 1 || row2 == 2) && (colom2 == 0 || colom2 == 1 || colom2 == 2)))           
					{
						start = n2.pop();
					}
					else
					{
						if (Games[row2][colom2] == 'X' || Games[row2][colom2] == 'O')                    
						{
							cout << "error" << endl;
							start = 1;
						}
						else
						{
							n2.push(row2);                              
							n2.push(colom2);                          
							Games[row2][colom2] = 'O';                     
							start = 1;
							Drow();
						}
					}
					break;                          
				}
				default: {                                   
					cout << "invalid input" << endl;
					start= 1; }
				}
			}
			Drow();                                  
			if (check())                             
			{
				system("pause");
				return 0;
			}
			player = 1;
			break;
		  }
		  default: {cout << "error , invalid number" << endl;                    
			cout << "who do you want first play 1-player1 2-player2 : ";
			cin >> player;
			start= 1;
		  }
		}
	}
	system("pause");
	return 0;
}


	
```

