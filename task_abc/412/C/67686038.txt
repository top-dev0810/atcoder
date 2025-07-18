#include<bits/stdc++.h>
using namespace std;

int main(){
  int T;
  cin >> T;
  
  while(T--){
    int N;
    cin >> N;
    vector<int> S(N);
    for(auto&& s:S)cin >> s;

    if(4 <= N) sort(S.begin() + 1,S.end()- 1);

    int ans = 2;
    int index = 0;
    int size = S[0];
    while(true){
        if(S[N-1] <= 2*size){
            cout << ans << "\n";
            break;
        }

        if(3 <= N){
            auto it = upper_bound(S.begin() + 1, S.end() - 1, 2*size);
            if (it != S.begin() + 1) {
                int i = distance(S.begin(), --it);
                if(i != index){
                    index = i;
                    ans++;
                    size = S[i];
                }else{
                    cout << "-1\n";
                    break;
                }

            } else {
                cout << "-1\n";
                break;
            }
        }else{
            cout << "-1\n";
            break;
        }
    }

  }


  return 0;
}