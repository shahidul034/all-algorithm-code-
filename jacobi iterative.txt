#include<iostream>
#include<stdio.h>
#include<string.h>
#include<cmath>
#define inf 0xfffffff
typedef long long int ll;//1507034
using namespace std;
double ans[100];
double Prev[100];
int main()
{
    freopen("in.txt","r",stdin);
    int n,m;
    cin>>n>>m;
    int VAL2;
    double mat[100][100];
    double B[100];
    for(int i=0; i<n; i++)
    {
        for(int j=0; j<m; j++)
        {
            cin>>mat[i][j];
        }
    }

    for(int i=0; i<n; i++)
    {

        cin>>B[i];
        //cout<<B[i]<<" ";
    }
    //cout<<endl;
    double VAL;
    int cnt=0;
    double ans2[100];
    memset(ans2,0,sizeof(ans2));
    int it=0;
    while(1)
    {
        for(int i=0; i<n; i++)
        {
            for(int j=0; j<m; j++)
            {
                if(i==j){VAL=mat[i][j];
                //cout<<i<<" i:j "<<j<<"  VAL: "<<VAL<<endl;
                }
                else
                {
                    VAL2=mat[i][j]*ans2[j];
                    ans[i]+=VAL2;
                }
            }
             //cout<<"ans: "<<ans[i]<<" "<<B[i]<<"/"<<VAL<<endl;
            //cout<<"VAL: "<<VAL<<endl;
            ans[i]=(B[i]-ans[i])/VAL;


        }


        for(int i=0;i<n;i++)Prev[i]=ans2[i];
        for(int i=0;i<n;i++){
			ans2[i]=ans[i];
        }
        int cnt=0;
        for(int i=0;i<n;i++){
			if(abs((ans2[i]-Prev[i])/ans2[i])<=.0001)cnt++;
        }
        if(cnt>=1)break;


    }

    for(int i=0;i<n;i++){
		cout<<ans2[i]<<endl;
    }



}
