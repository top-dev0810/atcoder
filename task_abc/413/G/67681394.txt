#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
typedef pair<int,int>PII;
const int N=1e6+10;
const int mod=998244353;
const int INF  = 0x3f3f3f3f;
const ll INFll  = 0x3f3f3f3f3f3f3f3f;
#define endl "\n" 

//vector<vector<int>>adj(N);



int dx[] = {1,-1,0,0,-1,1,1,-1};
int dy[] = {0,0,-1,1,-1,-1,1,1};


void solve()
{
    int h, w, k;
    cin >> h >> w >> k;

    
    map<PII,bool> st;
    map<PII,bool> v;

    for(int i = 1; i <= k; i ++) {
        int x, y; cin >> x >> y;
        st[{x, y}] = true;
    }

    queue<PII> q;
    q.push({h + 1, 0});
    v[{h + 1, 0}];

    for(int i = 1; i <= h; i ++) q.push({i, 0}), v[{i, 0}] = true;
    for(int i = 1; i <= w; i ++) q.push({h + 1, i}), v[{h + 1, i}] = true;

    

    while(q.size()) {  
        auto [x, y] = q.front(); q.pop();
        // cerr << x << " - " << y << endl;

        for(int i = 0; i < 8; i ++) {
            int tx = x + dx[i];
            int ty = y + dy[i];


            if(v.count({tx, ty})) continue;

            if(st.count({x, y})) {
                if(tx == 0 || ty == w + 1) {
                    cout << "No\n";
                    return;
                }
            }

            if(st.count({tx, ty}) && !v.count({tx, ty})) {
                q.push({tx, ty});
                v[{tx, ty}] = true;
            }

          
        }
    }

    cout << "Yes\n";

}


signed main()
{
    ios::sync_with_stdio(false);
    cin.tie(0),cout.tie(0);
    cout << setprecision(11) << fixed;
    int t;t=1;
    //cin>>t;
    for(int i=1;i<=t;i++){
        //printf("Case %d: ",i);
        solve();
    }
}