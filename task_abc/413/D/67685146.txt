#include<bits/stdc++.h>
using namespace std;

int main() {
    int T = 0;
    cin >> T;
    while(T--){
        int N = 0;
        cin >> N;
        vector<int> A(N);
        for(auto&& a:A) cin >> a;

        sort(A.begin(),A.end(),[](int a,int b){
            return abs(a) < abs(b);
        });

        if(ranges::count(A,A[0]) == N){
            cout << "Yes\n";
            continue;
        }

        if(const auto p_cnt{ranges::count(A,A[0])},n_cnt{ranges::count(A,-A[0])};
            p_cnt + n_cnt == N && min(p_cnt,n_cnt) == N/2){
            cout << "Yes\n";
            continue;
        }

        bool flag = true;
        for(int i = 0;i + 2 < N;++i){
            if(A[i]*A[i+2] != A[i+1]*A[i+1]){
                flag = false;
                break;
            }
        }
        if(flag){
            cout << "Yes\n";
        }else{
            cout << "No\n";
        }
    }

    return 0;
}