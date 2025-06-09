#include <bits/stdc++.h>

using namespace std;

#define endl '\n';
#define ll long long
#define rep(i, n) for (int i = 0; i < (int)(n); i++)

int init()
{
    cin.tie(nullptr);
    ios_base::sync_with_stdio(false);

    return 0;
}

int main()
{
    init();

    int N;
    cin >> N;

    vector<int> A(N);

    rep(i, N)
    {
        cin >> A.at(i);
    }

    auto answer = 0;

    rep(i, N + 1)
    {
        auto count = 0;

        for (auto a : A)
        {
            if (i <= a)
            {
                count++;
            }
        }

        if (count >= i)
        {
            answer = max(answer, i);
        }
    }

    cout << answer << endl;

    return 0;
}
