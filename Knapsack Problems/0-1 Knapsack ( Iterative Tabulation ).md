# 0-1 Knapsack Problem using Iterative Tabulation method

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
	for(int i=0;i<n+1;i++)
	{
		for(int j=0;j<w+1;j++)
		{
			if(i==0 || j==0)
			{
				t[i][j]=0;
			}
		}
	}

	for(int i=1;i<n+1;i++)
	{
		for(int j=1;j<w+1;j++)
		{
			if(wt[i-1]<j)
			{
				t[i][j]=max(val[i-1] + t[i-1][j-wt[i-1]] , t[i-1][j]);
			}
			else
			{
				t[i][j]=t[i-1][j];
			}
		}
	}
	return t[n][w];
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

**[Run Code](https://rextester.com/WFLWY95997)**
