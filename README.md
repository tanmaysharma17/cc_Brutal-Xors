#include <iostream>
#include<bits/stdc++.h>
#define ll long long int
using namespace std;

ll mod=1e9+7;


ll t,n;
ll _sub(ll x, ll y)
{
    x %= mod, y %= mod;
    return (x - y + mod) % mod;
}
ll _mul(ll x, ll y)
{
    x %= mod, y %= mod;
    return (x * 1ll * y) % mod;
}
ll _pow(ll x, ll y)
{
    if (y == 0)
        return 1;
    else if (y % 2 == 0)
    {
        ll _tmp = _pow(x, y / 2);
        return _mul(_tmp, _tmp);
    }
    else
        return _mul(x, _pow(x, y - 1));
}
ll _inv(ll p) { return _pow(p, mod - 2); }
int main() {
  // your code goes here
  cin>>t;
  while(t--){
      cin>>n;
      if(n==1){
          cout<<1<<endl;
          continue;
      }
      if(n==2){
          cout<<2<<endl;
          continue;
      }
      ll low=0;
      ll high=40;
      ll ans=high;
      while(low<high){
          ll mid=(low+high)/2;
          if(pow(2,mid)<=n){
              ans=mid;
              low=mid+1;
          }else{
              high=mid;
          }
      }
      ll p=_pow(2,ans);
     // cout<<ans<<endl;
      if(_pow(2,ans)==n){
        ll a=_mul(p,2);
        ll sub=_sub(a,1);
          cout<<sub<<endl;
      }else{
          ll a=_mul(2,p);
          cout<<a<<endl;
      }
  }
  return 0;
}
