#include <bits/stdc++.h>
using namespace std;

using ll = long long;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n;
    cin >> n;

    vector<ll> value(n + 1);

    for (int i = 1; i <= n; i++) {
        cin >> value[i];
    }

    vector<vector<pair<int, ll>>> adj(n + 1);

    for (int i = 0; i < n - 1; i++) {
        int u, v;
        ll w;

        cin >> u >> v >> w;

        adj[u].push_back({v, w});
        adj[v].push_back({u, w});
    }

    /*
        parent[u] = parent of u when tree is rooted at 1
        parentWeight[u] = weight of edge parent[u] -> u
        dist[u] = distance from node 1 to u
    */

    vector<int> parent(n + 1, 0);
    vector<ll> parentWeight(n + 1, 0);
    vector<ll> dist(n + 1, 0);

    vector<int> order;
    order.reserve(n);

    // ----------------------------
    // DFS from node 1
    // ----------------------------

    stack<int> st;

    st.push(1);
    parent[1] = -1;

    while (!st.empty()) {
        int u = st.top();
        st.pop();

        order.push_back(u);

        for (auto [v, w] : adj[u]) {

            if (v == parent[u])
                continue;

            parent[v] = u;
            parentWeight[v] = w;
            dist[v] = dist[u] + w;

            st.push(v);
        }
    }

    // ----------------------------
    // Calculate ans[1]
    // ----------------------------

    ll rootAnswer = 0;

    for (int i = 1; i <= n; i++) {
        rootAnswer += value[i] * dist[i];
    }

    // ----------------------------
    // Calculate subtree value sums
    // ----------------------------

    vector<ll> sub = value;

    /*
        Process children before parents.

        order contains parent before child,
        so traverse it backwards.
    */

    for (int i = n - 1; i > 0; i--) {

        int u = order[i];
        int p = parent[u];

        sub[p] += sub[u];
    }

    ll total = sub[1];

    // ----------------------------
    // Reroot DP
    // ----------------------------

    vector<ll> ans(n + 1);

    ans[1] = rootAnswer;

    /*
        Process parent before child.
    */

    for (int i = 1; i < n; i++) {

        int v = order[i];

        int u = parent[v];
        ll w = parentWeight[v];

        ans[v] =
            ans[u] +
            w * (total - 2LL * sub[v]);
    }

    // ----------------------------
    // Output
    // ----------------------------

    for (int i = 1; i <= n; i++) {
        if (i > 1)
            cout << ' ';

        cout << ans[i];
    }

    cout << '\n';

    return 0;
}
