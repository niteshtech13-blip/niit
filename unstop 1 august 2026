#include <bits/stdc++.h>
using namespace std;

const int MOD = 1000000007;

struct DSU {
    vector<int> p, sz;
    vector<long long> w;

    DSU(int n) {
        p.resize(n + 1);
        sz.assign(n + 1, 1);
        w.assign(n + 1, 1);
        iota(p.begin(), p.end(), 0);
    }

    long long modpow(long long a, long long e) {
        long long r = 1;
        while (e) {
            if (e & 1) r = r * a % MOD;
            a = a * a % MOD;
            e >>= 1;
        }
        return r;
    }

    long long inv(long long x) {
        return modpow(x, MOD - 2);
    }

    pair<int,long long> find(int x) {
        if (p[x] == x) return {x, 1};
        auto res = find(p[x]);
        w[x] = w[x] * res.second % MOD;
        p[x] = res.first;
        return {p[x], w[x]};
    }

    bool unite(int u, int v, long long r) {
        auto fu = find(u);
        auto fv = find(v);
        int ru = fu.first, rv = fv.first;
        long long wu = fu.second, wv = fv.second;

        if (ru == rv) {
            return wu * inv(wv) % MOD == r;
        }

        if (sz[ru] < sz[rv]) {
            p[ru] = rv;
            w[ru] = r * wv % MOD * inv(wu) % MOD;
            sz[rv] += sz[ru];
        } else {
            p[rv] = ru;
            w[rv] = wu % MOD * inv(r) % MOD * inv(wv) % MOD;
            sz[ru] += sz[rv];
        }
        return true;
    }

    pair<bool,long long> query(int u, int v) {
        auto fu = find(u);
        auto fv = find(v);
        if (fu.first != fv.first) return {false, 0};
        return {true, fu.second * inv(fv.second) % MOD};
    }
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int N, M;
    cin >> N >> M;

    DSU dsu(N);

    while (M--) {
        int t;
        cin >> t;
        if (t == 1) {
            int u, v;
            long long p, q;
            cin >> u >> v >> p >> q;
            long long r = p % MOD * dsu.inv(q % MOD) % MOD;
            if (dsu.unite(u, v, r))
                cout << "OK\n";
            else
                cout << "CONTRADICTION\n";
        } else {
            int u, v;
            cin >> u >> v;
            auto ans = dsu.query(u, v);
            if (!ans.first)
                cout << "UNKNOWN\n";
            else
                cout << ans.second << '\n';
        }
    }

    return 0;
}
