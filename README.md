# Data-Structure
见证期末

#include <iostream>
#include <bits/stdc++.h>
using  namespace std;
#define Maxn  100
//定义活动的类型
typedef  struct act_Node
{  int Id;       //活动ID
   int s_Time;   //活动开始时间
   int f_Time;   //活动结束时间
} ACND;
//  ********  Sort 函数  **********
//  ********  Select 函数 **********
bool cmp(ACND a,ACND b)
{
    if(a.f_Time==b.f_Time)
    return a.s_Time<b.s_Time;
        return a.f_Time<b.f_Time; //按照结束时间排序

}
void Sort(int n,ACND arr[])
{
    //快排
    sort(arr,arr+n,cmp);

}
void Select(int n,ACND arr[])//贪心
{
   // int x;
    //int i;

    int temp=0;
    cout<<arr[0].Id<<":"<<arr[0].s_Time<<"-"<<arr[0].f_Time<<endl;//最小的直接输出
    for(int i=1;i<n;i++)
    {
        if(arr[i].s_Time>=arr[temp].f_Time)//若该活动的开始时间大于等于上一个被安排活动的终止时间
        {
             temp=i;
        cout<<arr[i].Id<<":"<<arr[i].s_Time<<"-"<<arr[i].f_Time<<endl;
        }
    }
}
int main()
{  ACND arr[Maxn];
   int an,i;
   cin>>an;           //读入活动个数
   //读入各个活动的编号和占用资源的起止时间
   for(i=0;i<an;i++)
     cin>>arr[i].Id>>arr[i].s_Time>>arr[i].f_Time;
     Sort(an,arr);
     Select(an,arr);
  return 0;
}
