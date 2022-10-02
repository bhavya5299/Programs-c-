# Programs-c++



Divide a string in N equal parts

// C++ program to divide a string
// in n equal parts
#include <iostream>
#include <string.h>

using namespace std;

class gfg {

	// Function to print n equal parts of str
public:
	void divideString(char str[], int n)
	{

		int str_size = strlen(str);
		int i;
		int part_size;

		// Check if string can be divided in
		// n equal parts
		if (str_size % n != 0) {
			cout << "Invalid Input: String size";
			cout << " is not divisible by n";
			return;
		}

		// Calculate the size of parts to
		// find the division points
		part_size = str_size / n;
		for (i = 0; i < str_size; i++) {
			if (i % part_size == 0)
				cout << endl;
			cout << str[i];
		}
	}
};

// Driver code
int main()
{
	gfg g;

	// length od string is 28
	char str[] = "a_simple_divide_string_quest";

	// Print 4 equal parts of the string
	g.divideString(str, 4);
	return 0;
}

// This code is contributed by SoM15242



Rearrange a string so that all same characters become d distance away
// C++ program to rearrange a string so that all same
// characters become at least d distance away using STL
#include <bits/stdc++.h>
#include <iostream>
using namespace std;
typedef pair<char, int> PAIR;

// Comparator of priority_queue
struct cmp {
	bool operator()(const PAIR& a, const PAIR& b)
	{
		if(a.second < b.second) return true;
		else if(a.second > b.second) return false;
		else return a.first > b.first;
	}
};

void rearrange(char* str, int d)
{
	// Length of the string
	int n = strlen(str);

	// A structure to store a character and its frequency
	unordered_map<char, int> m;

	// Traverse the input string and store frequencies of
	// all characters.
	for (int i = 0; i < n; i++) {
		m[str[i]]++;
		str[i] = '\0';
	}

	// max-heap
	priority_queue<PAIR, vector<PAIR>, cmp> pq(m.begin(),
											m.end());

	// Now one by one extract all distinct characters from
	// heap and put them back in str[] with the d
	// distance constraint
	while (pq.empty() == false) {
		char x = pq.top().first;
		
		// Find the first available position in str[]
		int p = 0;
		while (str[p] != '\0')
			p++;
		
		// Fill x at p, p+d, p+2d, .. p+(frequency-1)d
		for (int k = 0; k < pq.top().second; k++) {
		
			// If the index goes beyond size, then string
			// cannot be rearranged.
			if (p + d * k >= n) {
				cout << "Cannot be rearranged";
				exit(0);
			}
			str[p + d * k] = x;
		}
		pq.pop();
	}
}

// Driver Code
int main()
{
	char str[] = "aabbcc";

	// Function call
	rearrange(str, 3);
	cout << str;
}



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
