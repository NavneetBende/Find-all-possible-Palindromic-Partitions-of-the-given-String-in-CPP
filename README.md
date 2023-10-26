# Find-all-possible-Palindromic-Partitions-of-the-given-String-in-CPP

All Possible Palindromic Partitions of the given String in C++
Today in this article we will discuss the program to Find all possible Palindromic partitions of the given String in C++ Programming Language. We will discuss both approach and code in this page.

All Possible Palindromic Partitions of the given String in C++
Algorithm:
We go through every substring starting from first character,
Check if it is palindrome.
If yes, then add the substring to solution.
And recur for remaining part.
Palindromic Partitions of given string in C++
Code in C++
Run
#include<bits/stdc++.h>
using namespace std;

bool isPalindrome(string str, int low, int high)
{
    while (low < high)
    {
        if (str[low] != str[high])
            return false;
        low++;
        high--;
    }
    return true;
}

void allPalPartUtil(vector<vector<string>>&allPart, vector<string> &currPart, int start, int n, string str)
{
    if (start >= n)
    {
        allPart.push_back(currPart);
        return;
    }
 
    for (int i=start; i<n; i++)
    {
        if (isPalindrome(str, start, i))
        {
            currPart.push_back(str.substr(start, i-start+1));
 
            allPalPartUtil(allPart, currPart, i+1, n, str);
          
            currPart.pop_back();
        }
    }
}

void allPalPartitions(string str)
{
    int n = str.length();
 
    vector<vector<string> > allPart;
 
    vector<string> currPart;
 
    allPalPartUtil(allPart, currPart, 0, n, str);
 
    for (int i=0; i<allPart.size(); i++ )
    {
        for (int j=0; j<allPart[i].size(); j++)
            cout << allPart[i][j] << " ";
        cout << "\n";
    }
}

int main()
{
    string str = "nitin";
    allPalPartitions(str);
    return 0;
}
Output :
n i t i n 
n iti n 
nitin 
