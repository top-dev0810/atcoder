#include <bits/stdc++.h>
using namespace std;
using ll = long long;

int main()
{
    int n, m;
    cin >> n >> m;
    vector<int> arr(n);
    for (int i = 0; i < m; i++)
    {
        int a;
        cin >> a;
        arr[a - 1]++;
    }

    if (arr[0] || arr[n - 1])
    {
        cout << "-1\n";
        return 0;
    }

    vector<int> p(n);
    iota(p.begin(), p.end(), 1);

    for (int i = 1; i < n - 1; i++)
    {
        if (arr[i])
        {
            swap(p[i], p[i + 1]);
        }
    }

    for (int i = 0; i < n; i++)
    {
        cout << p[i];
        if (i == n - 1)
        {
            cout << endl;
        }
        else
        {
            cout << " ";
        }
    }
    return 0;
}