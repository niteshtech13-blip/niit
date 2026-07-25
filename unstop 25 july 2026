#include <bits/stdc++.h>
using namespace std;

using ll = long long;

int m;
vector<vector<ll>> a;
vector<ll> dp;

ll solve(int mask) {
    if (mask == (1 << m) - 1) return 0;
    if (dp[mask] != -1) return dp[mask];

    int first = 0;
    while (mask & (1 << first)) first++;

    ll ans = 0;
    for (int j = first + 1; j < m; j++) {
        if (!(mask & (1 << j))) {
            ans = max(ans, a[first][j] + solve(mask | (1 << first) | (1 << j)));
        }
    }

    return dp[mask] = ans;
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int N;
    cin >> N;
    m = 2 * N;

    a.assign(m, vector<ll>(m));
    for (int i = 0; i < m; i++)
        for (int j = 0; j < m; j++)
            cin >> a[i][j];

    dp.assign(1 << m, -1);

    cout << solve(0);
    return 0;
}
