# test1
n_queen_problem

#include<bits/stdc++.h>
using namespace std;
int chess[11][11];

//incomplete

bool ispossible(int n, int row, int col)
{
    int i,j;
    for(i=row-1; i>=0; i--)
    {
        if(chess[i][col] == 1)
            return false;
    }
    for(i=row-1,j=col-1; i>=0 && j>=0; i--,j--)
    {
        if(chess[i][j] == 1)
            return false;
    }
    for(i=row-1,j=col+1; i>=0 && j<n; i--,j++)
    {
        if(chess[i][j] == 1)
            return false;
    }
    return true;
}

int nqueen_help(int n, int row, int &temp)
{
    if(row == n)
    {
        temp=1;
        cout<<'[';
        for(int i=0; i<n; i++)
        {
            
            for(int j=0; j<n; j++)
            {
                if(chess[i][j] == 1)
                    cout<<j+1<<" ";
            }
            
        }
        cout<<']'<<" ";
       // cout<<endl;
    // return;
    }
    for(int j=0; j<n; j++)
    {
        if(ispossible(n,row,j)){
            chess[row][j] = 1;
            nqueen_help(n,row+1,temp);
            chess[row][j] = 0;
        }
    }
    //return;
}

/*int place_queen(int n)
{
   // memset(array, 0, sizeof(array[0][0]) * m * n);
    memset(chess, 0, sizeof(chess[0][0]) *11 * 11);
    nqueen_help(n,0);
}*/
int main() {
	int t;
	cin>>t;
	while(t--)
	{
	    int n,temp=0;
	    cin>>n;
	    //place_queen(n);
	    memset(chess, 0, sizeof(chess[0][0]) *11 * 11);
        nqueen_help(n,0,temp);
        if(temp==0)
            cout<<"-1";
        cout<<endl;
	}
	return 0;
}
