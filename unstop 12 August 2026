#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    void solve() {
        int Q;
        cin >> Q;

        set<int> s;

        while (Q--) {
            string cmd;
            int x;
            cin >> cmd >> x;

            if (cmd == "ADD") {
                s.insert(x);
            }
            else if (cmd == "REMOVE") {
                s.erase(x);
            }
            else if (cmd == "EXISTS") {
                cout << (s.count(x) ? "YES" : "NO") << '\n';
            }
            else if (cmd == "BEFORE") {
                auto it = s.lower_bound(x);
                if (it == s.begin())
                    cout << "NONE\n";
                else {
                    --it;
                    cout << *it << '\n';
                }
            }
            else if (cmd == "AFTER") {
                auto it = s.upper_bound(x);
                if (it == s.end())
                    cout << "NONE\n";
                else
                    cout << *it << '\n';
            }
            else if (cmd == "POSITION") {
                if (x <= 0 || x > (int)s.size()) {
                    cout << "NONE\n";
                } else {
                    auto it = s.begin();
                    advance(it, x - 1);
                    cout << *it << '\n';
                }
            }
        }
    }
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    Solution obj;
    obj.solve();

    return 0;
}
