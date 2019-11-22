# BSTcode using c++ Templates
c++. A program that takes user inputs to Create, Modify, and print a BST.

Usage
This is a project that used templates in c++ to create a user based BST


#include "utility.h"
#include "Binary_node.h"
#include "Binary_tree.h"
#include "Search_tree.h"




//Sample code of main.cpp


#include "utility.h"
#include "Binary_node.h"
#include "Binary_tree.h"
#include "Search_tree.h"

//implement an increase function with x increasing by 1 each time
void increase(int& x)
{
	x = x + 1;//add 1 to x
}

int main() {
	string input = "";
	bool exit_now = false;
	Search_tree<int> stree;
	while (!exit_now) {
		cout << endl;
		cout << "***********************" << endl;
		cout << "Menu:" << endl;
		cout << "1. Incremental Insert" << endl;
		cout << "2. Incremental Delete" << endl;
		cout << "c. Clear tree" << endl;
		cout << "p. Print tree" << endl;
		cout << "h. Print tree height" << endl;
		cout << "s. Print tree size" << endl;
		cout << "i. Recursive inorder traversal" << endl;
		cout << "r. Recursive preorder traversal" << endl;
		cout << "o. Recursive postorder traversal" << endl;
		cout << "l. Print leaf count" << endl;
		cout << "x. Exit" << endl;
		cout << "***********************" << endl;

		getline(cin, input);

		if (input == "1") {
			cout << endl;
			cout << "Enter new integer keys to insert.  Enter \"q and then <Enter key>\" to quit and return menu." << endl;
			cout << endl;
			getline(cin, input);

			while (input != "q") {
				stree.insert(string_to_int(input));
				stree.print();
				getline(cin, input);
			}
		}
		else if (input == "2") {
			cout << endl;
			cout << "Enter integer keys to delete.  Enter \"q<Enter>\" to quit." << endl;
			cout << endl;
			getline(cin, input);
			while (input != "q") {
				stree.remove(string_to_int(input));
				stree.print();
				getline(cin, input);
			}
		}
		else if (input == "c")
			stree.clear();
		else if (input == "p")
			stree.print();
		else if (input == "h")
			cout << endl << "The height of the binary tree is " << stree.height() << endl;
		else if (input == "s")
			cout << endl << "The size (node count) of the binary tree is " << stree.size() << endl;
		else if (input == "x")
			exit_now = true;
		else if (input == "i")//check if input is i if so
		{
			cout << endl << "The inorder traversal of the binary tree is: ";//display the inorder traversal 
			void(*visit)(int& x);//create a visit function
			visit = *increase;
			stree.inorder(visit);//call the inorder function of stree
			stree.print();//print the tree
			cout << endl;
		}
		else if (input == "r")//check if input is r if so
		{
			cout << endl << "The pre-order traversal of the binary tree is: ";//display the preorder traversal
			void(*visit)(int& x);//create a visit function
			visit = *increase;
			stree.preorder(visit);//call the preorder function of stree
			stree.print();//print the tree
			cout << endl;
		}
		else if (input == "o")//check if input is o
		{
			cout << endl << "The post-order traversal of the binary tree is: ";//display the post order traversal
			void(*visit)(int& x);//create a visit function
			visit = *increase;
			stree.postorder(visit);//call the postorder function of the stree
			stree.print();//print the tree
			cout << endl;
		}
		else if (input == "l")//check if input is l
		{
			cout << endl << "The leaf count of the binary tree is: ";//display the leaf count
			cout << stree.getLeafCount();//by calling getLeafCount function
		}
	}
	return 0;
}
