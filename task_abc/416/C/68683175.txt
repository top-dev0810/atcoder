#include <bits/stdc++.h>

using namespace std;

using ii = pair<int,int>;
using vii = vector<ii>  ;
using vi = vector<int>  ;
#define ln  '\n'
#define ll long long
#define pb push_back
#define fi first
#define se second
#define sz(v) ((int)(v).size())
#define all(v) (v).begin(),(v).end()
#define rall(v) (v).rbegin(),(v).rend()
#define f(i, a, b)  for(ll i = (ll)a; i < (ll)b; i++)
#define fer(i, b, a)  for(ll i = (ll)a - 1; i >= (ll)b; i--)

void so(int test){
        int n,k,x;
        cin >> n >> k >> x;
        vector<string> v(n);
        f(i,0,n)cin >> v[i];

        auto su_bit = [&](int mask) -> int{
                int co = 0;
                f(i,0,12){
                        co += ((mask>>i)&1);
                }
                return co;
        };
        multiset<string> s;
        stack<vi> st;
        vi ga;
        st.push(ga);
        while(!st.empty()){
                vi to = st.top();st.pop();
                if(sz(to) == k){
                        string re;
                        f(i,0,k){
                                re += v[to[i]];
                        }
                        s.insert(re);
                        continue;
                }
                f(i,0,n){
                        to.pb(i);
                        st.push(to);
                        to.pop_back();
                }
        }
        int co = 1;
        for(auto ga : s){
                if(co == x){
                        cout << ga << ln;
                        return;
                }
                co++;
        }
        assert(false);
}

int main() {
	ios::sync_with_stdio(false);
	cin.tie(0);

	int tt = 1;
	int test = 1;
	while (tt--){
		so(test++);
	}
	return 0;
}
