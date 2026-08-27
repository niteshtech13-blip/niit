#include <bits/stdc++.h>
using namespace std;

struct Node {
    int child[2];
    int cnt;

    Node() {
        child[0] = child[1] = 0;
        cnt = 0;
    }
};

class PersistentTrie {
private:
    static const int MAX_BIT = 29;

    vector<Node> trie;

    // Create a copy of an existing node
    int cloneNode(int oldNode) {
        trie.push_back(trie[oldNode]);
        return (int)trie.size() - 1;
    }

public:
    PersistentTrie(int n) {
        /*
            Each insertion creates:

            1 root node
            + 30 nodes for bits 29 ... 0

            = 31 nodes
        */
        trie.reserve(1ULL + 1ULL * n * (MAX_BIT + 2));

        // Node 0 represents the empty/null node
        trie.push_back(Node());
    }

    int insert(int previousRoot, int value) {

        // Copy previous root
        int newRoot = cloneNode(previousRoot);

        trie[newRoot].cnt++;

        int currentNew = newRoot;
        int currentOld = previousRoot;

        for (int bit = MAX_BIT; bit >= 0; bit--) {

            int b = (value >> bit) & 1;

            // Child from previous version
            int oldChild = trie[currentOld].child[b];

            // Copy that child
            int newChild = cloneNode(oldChild);

            trie[newChild].cnt++;

            // Connect copied child to new version
            trie[currentNew].child[b] = newChild;

            currentNew = newChild;
            currentOld = oldChild;
        }

        return newRoot;
    }

    int getMaximumXor(
        int leftRoot,
        int rightRoot,
        int x
    ) {
        int answer = 0;

        int leftNode = leftRoot;
        int rightNode = rightRoot;

        for (int bit = MAX_BIT; bit >= 0; bit--) {

            int xBit = (x >> bit) & 1;

            // Opposite bit gives XOR bit = 1
            int preferred = xBit ^ 1;

            int leftPreferred =
                trie[leftNode].child[preferred];

            int rightPreferred =
                trie[rightNode].child[preferred];

            /*
                Number of elements belonging to [l, r]
                in the preferred branch.
            */
            int countInRange =
                trie[rightPreferred].cnt
                - trie[leftPreferred].cnt;

            if (countInRange > 0) {

                // We can make this XOR bit 1
                answer |= (1 << bit);

                leftNode = leftPreferred;
                rightNode = rightPreferred;
            }
            else {

                // Preferred bit unavailable.
                // Have to use same bit as x.

                int normal = xBit;

                leftNode =
                    trie[leftNode].child[normal];

                rightNode =
                    trie[rightNode].child[normal];
            }
        }

        return answer;
    }
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n;
    cin >> n;

    vector<int> a(n + 1);

    for (int i = 1; i <= n; i++) {
        cin >> a[i];
    }

    PersistentTrie trie(n);

    /*
        root[i] = trie containing:
        a[1], a[2], ..., a[i]
    */
    vector<int> root(n + 1);

    root[0] = 0;

    for (int i = 1; i <= n; i++) {
        root[i] = trie.insert(root[i - 1], a[i]);
    }

    int q;
    cin >> q;

    while (q--) {

        int l, r, x;
        cin >> l >> r >> x;

        cout << trie.getMaximumXor(
                    root[l - 1],
                    root[r],
                    x
                )
             << '\n';
    }

    return 0;
}
