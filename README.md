# Bop-The-Munchkin.cpp
#include <bits/stdc++.h>
using namespace std;
int sd,nowx,nowy;
int cnt;
int dx,dy,x,y;
int up_bd;
void jao(int indx[][3],int in,int chk)
{

    if((abs(dx-x))<abs(dy-y))
    {
        int temp = min(abs(dy-y),up_bd);
        if(dy>y)y+=temp;
        else y-=temp;
        up_bd-=temp;
        temp = min(abs(dx-x),up_bd);
        if(dx>x)x+=temp;
        else x-=temp;
        up_bd-=temp;

    }
    else
    {
        int temp = min(abs(dx-x),up_bd);
        if(dx>x)x+=temp;
        else x-=temp;
        up_bd-=temp;
        temp = abs(dy-y);
        temp = min(temp,up_bd);
        if(dy>y)y+=temp;
        else y-=temp;
        up_bd-=temp;
    }
    if(x==indx[in][0]&&y==indx[in][1] && chk==indx[in][2])cnt++;
    nowx=x,nowy=y;

}
int main()
{
  int n;
  cin>>n;
  string s;
  int indx[n][3];
  for(int i=0;i<n;i++)
  {

      cin>>s;
      cin>>indx[i][0]>>indx[i][1];
      if(s[1]=='1')indx[i][2]=1;
      else if (s[1]=='2')indx[i][2]=2;
      else indx[i][2]=3;
  }
  cin>>s;
  if(s[1]=='1')sd=1;
  else if(s[1]=='2')sd=2;
  else sd=3;

  for(int i=0;i<n;i++)
  {
    up_bd = sd*2;
    x=nowx;
    y=nowy;
    dx = indx[i][0];
    dy=indx[i][1];
    jao(indx,i,sd);
  }
  cout<<cnt<<endl;
  return 0;
}
