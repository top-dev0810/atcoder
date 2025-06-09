#include <bits/stdc++.h>
using namespace std;

int main() {
  string S;
  cin >> S;

  int A = 0;
  for (int i = 1; i < S.size(); i++) {
    if (S.at(i) == '-') {
      A++;
    } 
    
    if (S.at(i) == '|') {
      cout << A << " ";
      A = 0;
    }
  }

  cout << endl;

  return 0;
}