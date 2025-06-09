#include <bits/stdc++.h>
using namespace std;
typedef long long ll;typedef long double ld;typedef pair<int,int> pii;
#define fast ios::sync_with_stdio(0);cin.tie(0);cout.tie(0);
#define all(v) (v).begin(),(v).end()
#define rall(v) (v).rbegin(),(v).end()
#define F first
#define S second
const ll mod = 1e9+7;


vector<int> findcc(int node, vector<int> &vis, vector<vector<int>> &adj) {
    vector<int> nodes;
    function<void(int)> dfs = [&](int u) {
        vis[u]=1;
        nodes.push_back(u);
        for(int &v:adj[u]) {
            if (vis[v]==1) {
                continue;
            }
            dfs(v);
            
        }
    };
    dfs(node);
    return nodes;
}

vector<int> trav(vector<int> &nodes, vector<int>&vis, vector<int> &dadj) {
    int cyclelen = 0;
    int cnt = 0;
    int ops = 0;
    vector<int>path;
    function<void(int)> dfs = [&](int u) {
        vis[u]=1;
        cnt++;
        path.push_back(u);
        int v = dadj[u];
        if (v!=-1) {
            ops++;
            if (vis[v]==0) {
                dfs(v);
            } else if (vis[v]==1) {
                assert(cyclelen==0);
                int j=path.size()-1;
                while(j>=0 && path[j]!=v)
                    cyclelen++,j--;
                cyclelen++;
                if (cyclelen==1)
                    ops--;
            }
        }
        path.pop_back();
        vis[u]=2;
    };
    for(int &node:nodes) {
        if (vis[node]!=0)
            continue;
        dfs(node);
    }
    if (cnt==cyclelen) {
        return {1,ops};
    } else {
        return {0,ops};
    }
}

void solve() {
	int n;
    cin >> n;
    string s,t;
    cin >> s >> t;
    vector<int> dadj(26,-1);
    vector<vector<int>>uadj(26);
    for(int i=0;i<n;i++) {
        if (dadj[s[i]-'a']==-1 || dadj[s[i]-'a']==t[i]-'a') {
            dadj[s[i]-'a']=t[i]-'a';
        } else {
            cout <<-1 << "\n";
            return;
        }
    }
    for(int i=0;i<26;i++) {
        if (dadj[i]==-1)
            continue;
        if (i==dadj[i]) {
            uadj[i].push_back(dadj[i]);
        } else {
            uadj[i].push_back(dadj[i]);
            uadj[dadj[i]].push_back(i);
        }
    }
    vector<vector<int>> cc;
    vector<int> vis(26,0);
    for(int i=0;i<26;i++) {
        if (vis[i]!=0)
            continue;
        cc.push_back(findcc(i,vis,uadj));
    }
    vector<vector<int>> tt;
    fill(all(vis),0);
    for(int i=0;i<cc.size();i++) {
        tt.push_back(trav(cc[i],vis,dadj));
    }
    sort(all(tt));
    bool freenode = false;
    int ans =0 ;
    for(int i=0;i<tt.size();i++) {
        if (tt[i][0]==0) {
            freenode=true;
            ans+=tt[i][1];
        } else {
            if (tt[i][1]>0 && freenode) {
                ans+=tt[i][1]+1;
            } else if (tt[i][1]>0) {
                cout << -1 << "\n";
                return;
            }
        }
    }
    cout << ans << "\n";
}


int main() {
    fast;
    int t = 1;
    while(t--){
    	solve();
    }
    return 0;
}
