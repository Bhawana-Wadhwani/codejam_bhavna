# codejam_bhavna
Google code jam codes
#vestigium

t: Number of test cases

t = int(input())
for a in range(1, t+1):
l=int(input())
lst=[]
for j in range(1,l+1):
lst.append(list(map(int, input().split())))
tr=0
for i in range(1,l+1):
for j in range(1,l+1):
if i==j:
tr=tr+lst[i-1][j-1]
rc=0
for i in range(1,l+1):
arr=lst[i-1]
flag=True
for j in range(1,l+1):
if j not in arr:
flag=False
if flag is False:
rc=rc+1

cc=0
for i in range(0,l):
    arr=[]
    for j in range(0,l):
        arr.append(lst[j][i])
    flag=True
    for j in range(1,l+1):
        if j not in arr:
            flag=False
    if flag is False:
        cc=cc+1

print("Case #{}: {} {} {}".format(a, tr, rc, cc))
##Nesting Depth
t = int(input())
for i in range(t):
s = input()
brac = 0
ne = ""
if(len(s) == 1):
ne += "("*int(s) + s + ")"*int(s)
else:
for index,n in enumerate(s):
if(index == 0):
lbrac = int(n)
rbrac = int(n)-int(s[index+1])
elif(index == (len(s)-1)):
lbrac = int(n)-int(s[index-1])
if(lbrac > 0):
ne += "("*lbrac
brac+=lbrac
rbrac = brac
ne+=n
ne += ")"*rbrac
break

        else:
            lbrac = int(n)-int(s[index-1])
            rbrac = int(n)-int(s[index+1])
        if(lbrac>0):
            ne += "("*lbrac
            brac+=lbrac
        ne += n
        if(rbrac>=0):
            ne += ")"*rbrac
            brac -= rbrac

print("Case #{}: {}".format(i+1,ne))
//Parenting Partering Returns
#include<bits/stdc++.h>
#include
using namespace std;
#define ll long long
#define double long double
#define endl '\n'
#define sz(x) (int)(x).size()

#define pb push_back
#define pf push_front
#define lb(v,n) lower_bound(all((v)),(n))
#define ub(v,n) upper_bound(all((v)),(n))

#define vi vector
#define vii vector
#define viiii vector<pair<pii,pii>>

#define mi map<int,int>
#define mii map<pii,int>

#define pii pair<int,int>
#define piii pair<int,pair<int,int> >
#define piiii pair<pii,pii>
#define fi first
#define se second
#define mp make_pair
#define all(a) (a).begin(),(a).end()
#define rall(a) (a).rbegin(),(a).rend()

#define rep(X,Y) for (int (X) = 0;(X) < (Y);++(X))
#define reps(X,S,Y) for (int (X) = S;(X) < (Y);++(X))
#define rrep(X,Y) for (int (X) = (Y)-1;(X) >=0;--(X))
#define rreps(X,S,Y) for (int (X) = (Y)-1;(X) >= (S);--(X))
#define repe(X,Y) for ((X) = 0;(X) < (Y);++(X))
#define toit ios::sync_with_stdio(0);cin.tie(0);

int gcd(int a, int b) { if (b == 0) return a; return gcd(b , a % b); }
bool mod(double a,double b) {return a/b - floor(a/b);}

int occurs(vi v,int n){
auto it=lb(v,n);auto it1=ub(v,n);int x=it1-it;return x;}

double max(double a,double b){
return a<b ? b:a;
}

int main()
{toit
int t;
cin>>t;
int tc=0;
while(t--){
tc++;
int n;
cin>>n;
map<pii,int>mp;
vectorv;
rep(i,n){
int x,y;
cin>>x>>y;
mp.insert({pii(x,y),i});
v.pb(pii(x,y));
}
sort(all(v));
string ans="";
rep(i,n) ans+="C";

    ans[mp[{v[0].first,v[0].second}]]='C';
    
    int etimec=v[0].second,etimej,flag=0,im=0;
    for(int i=1;i<n;i++)
    {
        if(v[i].first>=etimec)
        {
            ans[mp[{v[i].first,v[i].second}]]='C';
            etimec=v[i].second;
        }
        else if(v[i].first<etimec && flag==0)
        {
            flag=1;
            etimej=v[i].second;
            ans[mp[{v[i].first,v[i].second}]]='J';
        }
        else if(v[i].first<etimec && v[i].first>=etimej)
        {
            etimej=v[i].second;
            ans[mp[{v[i].first,v[i].second}]]='J';
        }
        else if(v[i].first<etimec && v[i].first<etimej)
        {
            im=1;
            break;
        }
    }
    if(im==1) cout<<"Case #"<<tc<<": "<<"IMPOSSIBLE"<<endl;
    else
    cout<<"Case #"<<tc<<": "<<ans<<endl;
    
    
    
}
return 0;
}

//Indicium
#include <bits/stdc++.h>

using namespace std;

int sqr[60][60], n, k, t;
bool row_safe[60][60], col_safe[60][60], solved;

void solver(int row, int col, int m) {
if (row == n && col == n + 1 && m == k && !solved) {
solved = true;
cout << "Case #" << t << ": " << "POSSIBLE\n";
for (int i = 1; i <= n; ++i) {
for (int j = 1; j <= n; ++j) {
cout << sqr[i][j] << " ";
}
cout << "\n";
}
return;
} else if (row > n) {
return;
} else if (col > n) {
solver(row + 1, 1, m);
}
for (int i = 1; i <= n && !solved; ++i) {
if (!row_safe[row][i] && !col_safe[col][i]) {
row_safe[row][i] = col_safe[col][i] = true;
if (row == col) {
m += i;
}
sqr[row][col] = i;

        solver(row, col + 1, m);

        row_safe[row][i] = col_safe[col][i] = false;
        if (row == col) {
            m -= i;
        }
        sqr[row][col] = 0;
    }
}
}

int main() {
int T;
scanf(" %d", &T);
for (t = 1; t <= T; ++t) {
scanf(" %d %d", &n, &k);
solver(1, 1, 0);
if (!solved) {
cout << "Case #" << t << ": " << "IMPOSSIBLE\n";
}
solved = false;
}
return 0;
}
