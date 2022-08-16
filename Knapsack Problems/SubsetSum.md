# Subset Sum problem using recursion

**Description :** This program shows demonstration of subset sum problem using recursion, where we are inputing an array and a value of sum and finding it whether there exists a subset whose sum can make the value equal to the sum.

**Example**

```cpp
#include<iostream>
using namespace std;

bool subsetSum(int a[],int n,int sum)
{
	if(n==0)
	{
		return false;
	}
	if(sum==0)
	{
		return true;
	}
	if(a[n-1]<=sum)
	{
		return (subsetSum(a,n-1,sum-a[n-1]) || subsetSum(a,n-1,sum));
	}
	else
	{
		return (subsetSum(a,n-1,sum));
	}
}


int main()
{
	int n,sum;
	cout<<"Enter the size of the array"<<endl;
	cin>>n;
	int a[n];
	cout<<"Enter the array"<<endl;
	for(int i=0;i<n;i++)
	{
		cin>>a[i];
	}
	cout<<"Enter the value of sum"<<endl;
	cin>>sum;
	if(subsetSum(a,n,sum))
	{
		cout<<"Possible to make a subset"<<endl;
	}
	else
	{
		cout<<"Not Possible to make a subset"<<endl;
	}
}
```

**[Run Code](https://rextester.com/DICL86269)**
