#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    int n, K;
    cin >> n >> K;

    vector<int> team(n), rating(n);
    unordered_map<int, vector<int>> positions;

    for (int i = 0; i < n; i++) {
        cin >> team[i] >> rating[i];
        positions[team[i]].push_back(i);
    }

    vector<int> wait(n, -1);

    for (auto &entry : positions) {
        const vector<int>& pos = entry.second;
        vector<int> st;

        for (int j = (int)pos.size() - 1; j >= 0; j--) {
            int idx = pos[j];

            // Find the next strictly greater rating.
            while (!st.empty() &&
                   rating[st.back()] <= rating[idx]) {
                st.pop_back();
            }

            if (!st.empty()) {
                wait[idx] = st.back() - idx;
            }

            st.push_back(idx);
        }
    }

    // Print wait values.
    for (int i = 0; i < n; i++) {
        if (i) cout << ' ';
        cout << wait[i];
    }
    cout << '\n';

    // Collect valid entries for leaderboard.
    vector<pair<int, int>> leaderboard;

    for (int i = 0; i < n; i++) {
        if (wait[i] != -1) {
            leaderboard.push_back({wait[i], i + 1});
        }
    }

    // Longer wait first; ties go to earlier entry.
    sort(leaderboard.begin(), leaderboard.end(),
         [](const auto& a, const auto& b) {
             if (a.first != b.first)
                 return a.first > b.first;
             return a.second < b.second;
         });

    int count = min(K, (int)leaderboard.size());

    for (int i = 0; i < count; i++) {
        if (i) cout << ' ';
        cout << leaderboard[i].second;
    }
    cout << '\n';

    return 0;
}
