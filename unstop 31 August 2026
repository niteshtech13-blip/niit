#include <bits/stdc++.h>
using namespace std;

using ll = long long;

struct Edge {
    int u;
    int v;
    ll w;
};

class DSU {
private:
    vector<int> parent;
    vector<int> sz;

public:
    DSU(int n) {
        parent.resize(n + 1);
        sz.assign(n + 1, 1);

        for (int i = 1; i <= n; i++) {
            parent[i] = i;
        }
    }

    int find(int x) {
        if (parent[x] == x) {
            return x;
        }

        return parent[x] = find(parent[x]);
    }

    bool unite(int a, int b) {
        int parentA = find(a);
        int parentB = find(b);

        // Already connected
        if (parentA == parentB) {
            return false;
        }

        // Union by size
        if (sz[parentA] < sz[parentB]) {
            swap(parentA, parentB);
        }

        parent[parentB] = parentA;
        sz[parentA] += sz[parentB];

        return true;
    }
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n, m;
    cin >> n >> m;

    vector<Edge> edges(m);

    for (int i = 0; i < m; i++) {
        cin >> edges[i].u
            >> edges[i].v
            >> edges[i].w;
    }

    // Sort edges by increasing cost
    sort(edges.begin(), edges.end(),
         [](const Edge& a, const Edge& b) {
             return a.w < b.w;
         });

    DSU dsu(n);

    ll totalCost = 0;
    int edgesUsed = 0;

    for (const Edge& edge : edges) {

        if (dsu.unite(edge.u, edge.v)) {
            totalCost += edge.w;
            edgesUsed++;

            // MST is complete
            if (edgesUsed == n - 1) {
                break;
            }
        }
    }

    // If n-1 edges were not found,
    // the graph is disconnected.
    if (edgesUsed != n - 1) {
        cout << -1 << '\n';
    } else {
        cout << totalCost << '\n';
    }

    return 0;
}
