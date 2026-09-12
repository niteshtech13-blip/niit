#include <bits/stdc++.h>
using namespace std;

struct TrieNode {
    int child[36];
    bool isEnd;

    TrieNode() {
        memset(child, -1, sizeof(child));
        isEnd = false;
    }
};

// Convert A-Z / 0-9 to an index
int getIndex(char c) {
    if (c >= 'A' && c <= 'Z')
        return c - 'A';

    return 26 + (c - '0');
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int N;
    cin >> N;

    vector<TrieNode> trie;
    trie.emplace_back(); // root

    long long total = 0;

    for (int query = 0; query < N; query++) {
        string s;
        cin >> s;

        int node = 0;
        int longestPrefix = 0;
        bool pathExists = true;

        // Find duplicate and longest registered prefix
        for (int i = 0; i < (int)s.length(); i++) {
            int c = getIndex(s[i]);

            if (trie[node].child[c] == -1) {
                pathExists = false;
                break;
            }

            node = trie[node].child[c];

            // A complete previously registered call sign
            // is a valid prefix.
            if (trie[node].isEnd) {
                longestPrefix = i + 1;
            }
        }

        // If the complete string exists and is registered,
        // it is a duplicate.
        if (pathExists && trie[node].isEnd) {
            cout << -1 << '\n';
            continue;
        }

        int score = (int)s.length() - longestPrefix;

        cout << score << '\n';

        total += score;

        // Insert this new call sign
        node = 0;

        for (char ch : s) {
            int c = getIndex(ch);

            if (trie[node].child[c] == -1) {
                trie[node].child[c] = trie.size();
                trie.emplace_back();
            }

            node = trie[node].child[c];
        }

        trie[node].isEnd = true;
    }

    cout << "Total: " << total << '\n';

    return 0;
}
