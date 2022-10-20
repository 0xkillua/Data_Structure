#  Stack 

## A stack is an abstract data structure
 that contains a collection of elements

##Stack implements the LIFO mechanism i.e.

the element that is pushed at the end is popped out first.

Some of the principle operations in the stack are :

Push - This adds a data value to the top of the stack.

Pop - This removes the data value on top of the stack.

Peek - This returns the top data value of the stack.

full - this check  the stack is full or not.

Empety - this check  the stack is empety or not.

 ## stack Implementation Using Fixed Length Array

## Explanation
```c++
#include<bits/stdc++.h>
#define max_size 100 
using namespace std; 
class stac {
private:
int items[max_size]; 
int top;
public:
     stac () { top = -1; }

	void push(int element); 
	int pop();
	bool is_empty();
	bool is_full();
	int peek() { return items[top]; }/*return top of stack */
	void print_all_elements();
};
/* Push Function*/
void stac::push(int element) {
if (is_full())
{
	cout << "Stack is overflow";
	return;
} top++;
items[top] = element;
}
/*Pop Function*/ 
int stac::pop()
{
if (is_empty()) 
{
	cout << "Stack is underflow";
	return -1;
}
int element= items[top];
top--; 
return element;
}
/* Is_empty Function*/  
bool stac::is_empty() {
	if (top == -1) return true;
	return false;
}
/*Is_full Function*/
bool stac::is_full() {
if (top == max_size - 1) return 1;
return 0; }
/*print element */
void stac::print_all_elements() 
{
	for (int i = 0; i < top - 1; i++)
		cout << items[i] << " ";
}
void main()
{


/* in the Exercise */

}
```
## stack Implementation Using Dynamic Length Array
```c++
#include<bits/stdc++.h>
using namespace std; 
class stac {
private:
	int Max_s;
    int *items; 
    int top;
public:
	stac();
	 ~stac();
	void push(int element); 
	int pop();
	bool is_empty();
	bool is_full();
	int peek() { return items[top]; }/*return top of stack*/
	void print_all_elements();
};
/*size of stack constructor and declare top*/
stac::stac()
{
	cout << "Enter size of stack";
	cin >> Max_s;
	items = new int[Max_s];
	top = -1;
}
// Stack destructor Function 
stac::~stac () {
delete items;
items = NULL;
top = -1;
Max_s = 0;
} 
/* Push Function*/
void stac::push(int element) {
if (is_full())
{
	cout << "Stack is overflow";
	return;
} top++;
items[top] = element;
}
/*Pop Function*/ 
int stac::pop()
{
if (is_empty()) 
{
	cout << "Stack is underflow";
	return -1;
}
int element= items[top];
top--; 
return element;
}
/* Is_empty Function*/  
bool stac::is_empty() {
	if (top == -1) return true;
	return false;
}
/*Is_full Function*/
bool stac::is_full() {
if (top == Max_s- 1) return 1;
return 0; }
/*print element */
void stac::print_all_elements() 
{
	for (int i = 0; i < top - 1; i++)
		cout << items[i] << " ";
}
void main()
{


/* in the Exercise */

}
```
##
