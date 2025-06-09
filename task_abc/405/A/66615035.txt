#include <iostream>
using namespace std;

void solve(){
    int R, X; cin >> R >> X;
    
    if (X == 1){
        if (1600 <= R && R <= 2999){
            cout << "Yes" << endl;
        } else {
            cout << "No" << endl;
        }
        return;
    } else {
        if (1200 <= R && R <=2399){
            cout << "Yes" << endl;
        } else {
            cout << "No" << endl;
        }
        return;
    }

}

int main(){
    solve();
    return 0;
}
