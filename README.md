# Programs-c++


Program to find second most frequent character
#include <bits/stdc++.h>
using namespace std;
#define NO_OF_CHARS 256

// CPP function to find the
// second most frequent character
// in a given string 'str'
char getSecondMostFreq(string str)
{
	// count number of occurrences of every character.
	int count[NO_OF_CHARS] = {0}, i;
	for (i = 0; str[i]; i++)
		(count[str[i]])++;

	// Traverse through the count[] and
	// find second highest element.
	int first = 0, second = 0;
	for (i = 0; i < NO_OF_CHARS; i++)
	{
		/* If current element is smaller
		than first then update both
		first and second */
		if (count[i] > count[first])
		{
			second = first;
			first = i;
		}

		/* If count[i] is in between first
		and second then update second */
		else if (count[i] > count[second] &&
				count[i] != count[first])
			second = i;
	}

	return second;
}

// Driver code
int main()
{
	string str = "geeksforgeeks";
	char res = getSecondMostFreq(str);
	if (res != '\0')
		cout << "Second most frequent char is " << res;
	else
		cout << "No second most frequent character";
	return 0;
}

// This code is contributed by rathbhupendra

Print reverse of a string using recursion
// C++ program to reverse a string using recursion
#include <bits/stdc++.h>
using namespace std;

/* Function to print reverse of the passed string */
void reverse(string str)
{
	if(str.size() == 0)
	{
		return;
	}
	reverse(str.substr(1));
	cout << str[0];
}

/* Driver program to test above function */
int main()
{
	string a = "Geeks for Geeks";
	reverse(a);
	return 0;
}

// This is code is contributed by rathbhupendra

Write a program to print all permutations of a given string

// C++ program to print all
// permutations with duplicates allowed
#include <bits/stdc++.h>
using namespace std;


// Function to print permutations of string
// This function takes three parameters:
// 1. String
// 2. Starting index of the string
// 3. Ending index of the string.
void permute(string a, int l, int r)
{
	// Base case
	if (l == r)
		cout<<a<<endl;
	else
	{
		// Permutations made
		for (int i = l; i <= r; i++)
		{

			// Swapping done
			swap(a[l], a[i]);

			// Recursion called
			permute(a, l+1, r);

			//backtrack
			swap(a[l], a[i]);
		}
	}
}

// Driver Code
int main()
{
	string str = "ABC";
	int n = str.size();
	permute(str, 0, n-1);
	return 0;
}

// This is code is contributed by rathbhupendra
