#include <bits/stdc++.h>
using namespace std;

const int MAXN = 1e5 + 5;
vector<int> tree[MAXN];
string label;
map<int, int> freq;
long long result = 0;

void dfs(int node, int parent, int mask) {
    mask ^= (1 << (label[node] - 'a'));
    
    // Count all previously seen paths with same mask (perfect palindrome)
    result += freq[mask];

    // Count all masks differing by one bit (only one char with odd count)
    for (int i = 0; i < 26; ++i) {
        int flipped = mask ^ (1 << i);
        result += freq[flipped];
    }

    // Mark current path mask
    freq[mask]++;

    for (int child : tree[node]) {
        if (child != parent) {
            dfs(child, node, mask);
        }
    }

    // Unmark when backtracking
    freq[mask]--;
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n;
    cin >> n;
    cin >> label;
    for (int i = 0; i < n - 1; ++i) {
        int u, v;
        cin >> u >> v;
        u--; v--;
        tree[u].push_back(v);
        tree[v].push_back(u);
    }

    freq[0] = 1; // base case: empty path is palindrome
    dfs(0, -1, 0);
    cout << result << "\n";
    return 0;
}
