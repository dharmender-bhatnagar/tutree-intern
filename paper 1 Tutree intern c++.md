# tutree-intern
Q1- Find the smallest and second smallest elements in an array.

Explanation- Write an efficient C program to find smallest and second smallest element in an array

Example:

Input: arr[] = {12, 13, 1, 10, 34, 1}
Output: The smallest element is 1 and
second Smallest element is 10

solution 1 :
#include <bits/stdc++.h>
using namespace std; 
 
void print2Smallest(int arr[], int arr_size)
{
    int i, first, second;
    if (arr_size < 2)
    {
        cout<<" Invalid Input ";
        return;
    }
   first = second = INT_MAX;
    for (i = 0; i < arr_size ; i ++)
    {
        if (arr[i] < first)
        {
            second = first;
            first = arr[i];
        }
        else if (arr[i] < second && arr[i] != first)
            second = arr[i];
    }
    if (second == INT_MAX)
        cout << "There is no second smallest element\n";
    else
        cout << "The smallest element is " << first << " and second Smallest element is " << second << endl;
}
 

int main()
{
    int arr[] = {12, 13, 1, 10, 34, 1};
    int n = sizeof(arr)/sizeof(arr[0]);
    print2Smallest(arr, n);
    return 0;
}
********************************************************************************************************************************
Q2-Find median in a stream of integers (running integers)

Explanation-
Given that integers are read from a data stream. Find median of elements read so for in efficient way. For simplicity assume there are no duplicates. For example, let us consider the stream 5, 15, 1, 3 …

After reading 1st element of stream - 5 -> median - 5
After reading 2nd element of stream - 5, 15 -> median - 10
After reading 3rd element of stream - 5, 15, 1 -> median - 5
After reading 4th element of stream - 5, 15, 1, 3 -> median - 4, so on...

solution 2 :

#include <bits/stdc++.h>
using namespace std; 
void printRunningMedian(int arr[], int n){
    if(n==0)
    {
        return;
    }
    priority_queue<int> s; 
    priority_queue<int,vector<int>,greater<int> > g; 
  
    int ans = arr[0]; 
    s.push(arr[0]); 
    cout << ans << " "; 
    for (int i=1; i < n; i++) 
    { 
        int x = arr[i]; 
        if (s.size() > g.size()) 
        { 
            if (x < ans) 
            { 
                g.push(s.top()); 
                s.pop(); 
                s.push(x); 
            } 
            else
                g.push(x); 
  
            ans = (s.top() + g.top())/2.0; 
        } 
        else if (s.size()==g.size()) 
        { 
            if (x < ans) 
            { 
                s.push(x); 
                ans = (int)s.top(); 
            } 
            else
            { 
                g.push(x); 
                ans = (int)g.top(); 
            } 
        } 
        else
        { 
            if (x > ans) 
            { 
                s.push(g.top()); 
                g.pop(); 
                g.push(x); 
            } 
            else
                s.push(x); 
  
            ans = (s.top() + g.top())/2.0; 
        } 
  
        cout << ans << " "; 
    } 
}
int main() {
    int n;
    cin >> n;

    int* arr = new int[n];

    for (int i = 0; i < n; ++i) {
        cin >> arr[i];
    }

    findMedian(arr,n);

    delete[] arr;
}



