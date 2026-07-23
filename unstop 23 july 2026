#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int N;
    cin >> N;

    vector<vector<long long>> cost(N + 1, vector<long long>(N + 1));

    for (int i = 0; i <= N; i++) {
        for (int j = 0; j <= N; j++) {
            cin >> cost[i][j];
        }
    }

    const long long INF = 1e18;
    int FULL = 1 << N;

    vector<vector<long long>> dp(FULL, vector<long long>(N + 1, INF));

    for (int i = 1; i <= N; i++) {
        dp[1 << (i - 1)][i] = cost[0][i];
    }

    for (int mask = 0; mask < FULL; mask++) {
        for (int u = 1; u <= N; u++) {
            if (dp[mask][u] == INF) continue;

            for (int v = 1; v <= N; v++) {
                if (!(mask & (1 << (v - 1)))) {
                    int newMask = mask | (1 << (v - 1));
                    dp[newMask][v] = min(dp[newMask][v],
                                         dp[mask][u] + cost[u][v]);
                }
            }
        }
    }

    long long ans = INF;
    int allVisited = FULL - 1;

    for (int u = 1; u <= N; u++) {
        ans = min(ans, dp[allVisited][u] + cost[u][0]);
    }

    cout << ans << endl;
    return 0;
}
