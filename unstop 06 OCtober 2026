#include <bits/stdc++.h>
using namespace std;

struct Request {
    int deadline;
    long long priority;
    int index;
};

class SegmentTree {
private:
    int n;
    vector<int> tree;

    void build(int node, int l, int r, const vector<int>& capacity) {
        if (l == r) {
            tree[node] = capacity[l];
            return;
        }

        int mid = (l + r) / 2;

        build(node * 2, l, mid, capacity);
        build(node * 2 + 1, mid + 1, r, capacity);

        tree[node] = max(tree[node * 2], tree[node * 2 + 1]);
    }

    void update(int node, int l, int r, int pos) {
        if (l == r) {
            tree[node]--;
            return;
        }

        int mid = (l + r) / 2;

        if (pos <= mid)
            update(node * 2, l, mid, pos);
        else
            update(node * 2 + 1, mid + 1, r, pos);

        tree[node] = max(tree[node * 2], tree[node * 2 + 1]);
    }

    // Find the rightmost position <= qR having capacity > 0.
    int query(int node, int l, int r, int qR) {
        if (l > qR || tree[node] <= 0)
            return 0;

        if (l == r)
            return l;

        int mid = (l + r) / 2;

        // Search right side first to get the latest possible day.
        if (qR > mid) {
            int result = query(node * 2 + 1, mid + 1, r, qR);
            if (result != 0)
                return result;
        }

        return query(node * 2, l, mid, qR);
    }

public:
    SegmentTree(const vector<int>& capacity) {
        n = (int)capacity.size() - 1;
        tree.assign(4 * n + 5, 0);
        build(1, 1, n, capacity);
    }

    int findLatest(int deadline) {
        return query(1, 1, n, deadline);
    }

    void occupy(int day) {
        update(1, 1, n, day);
    }
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int D, T;
    cin >> D >> T;

    vector<int> capacity(D + 1);

    for (int day = 1; day <= D; day++) {
        cin >> capacity[day];
    }

    vector<Request> requests(T);

    for (int i = 0; i < T; i++) {
        cin >> requests[i].deadline >> requests[i].priority;
        requests[i].index = i;
    }

    // Highest priority first.
    // For equal priority, earlier input order first.
    sort(requests.begin(), requests.end(),
         [](const Request& a, const Request& b) {
             if (a.priority != b.priority)
                 return a.priority > b.priority;

             return a.index < b.index;
         });

    SegmentTree segTree(capacity);

    vector<int> assigned(T, 0);

    long long totalPriority = 0;

    for (const Request& req : requests) {
        int day = segTree.findLatest(req.deadline);

        if (day != 0) {
            assigned[req.index] = day;
            totalPriority += req.priority;

            segTree.occupy(day);
        }
    }

    cout << totalPriority << '\n';

    for (int i = 0; i < T; i++) {
        if (i > 0)
            cout << ' ';

        cout << assigned[i];
    }

    cout << '\n';

    return 0;
}
