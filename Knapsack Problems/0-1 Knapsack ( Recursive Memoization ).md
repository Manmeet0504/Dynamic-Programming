# 0-1 Knapsack Problem using recursive memoization

**Description :** This program shows demonstration of simple 0-1 Knapsack problem. Here we are taking 2 arrays ( weight and value ) and then printing the max profit that can be achieved from selecting the values

**Example**

```cpp
#include<iostream>
#include <bits/stdc++.h>
#include<algorithm>
using namespace std;

int knapsack(int wt[],int val[],int w,int n)
{
	int t[n+1][w+1];
	memset(t,-1,sizeof(t));
	if(n==0 || w==0)
	{
		return 0;
	}
	if(t[n][w]!=-1)
	{
		return t[n][w];
	}
	if(wt[n-1]<w)
	{
		return (t[n][w] = max(val[n-1] + knapsack(wt,val,w-wt[n-1],n-1) , knapsack(wt,val,w,n-1)));
	}
	else
	{
		return (t[n][w] = knapsack(wt,val,w,n-1));
	}
}

int main()
{
	int n,w;
	cout<<"Enter the size of the array"<<endl;
	cin>>n;
	cout<<"Enter the weight of the knapsack"<<endl;
	cin>>w;
	int wt[n];
	int val[n];
	cout<<"Enter the weight array"<<endl;
	for(int i=0;i<n;i++)
	{
		cin>>wt[i];
	}
	cout<<"Enter the value array"<<endl;
	for(int i=0;i<n;i++)
	{
		cin>>val[i];
	}

	cout<<"Maximum Profit -> "<<knapsack(wt,val,w,n);
}
```

**[Run Code](https://rextester.com/QUCRG98514)**
