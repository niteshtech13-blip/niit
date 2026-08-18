#include <iostream>
#include <vector>

using namespace std;

long long countArrangements(int n, long long k, const vector<long long>& sightings) {
    long long MOD = 1000000007;
    vector<long long> dp(n + 1, 0);
    dp[0] = 1;
    
    int L = 0;
    long long current_window_sum = 0;
    long long dp_sum = 1;
    
    for (int i = 1; i <= n; ++i) {
        current_window_sum += sightings[i - 1];
        
        while (current_window_sum > k && L < i) {
            current_window_sum -= sightings[L];
            dp_sum = (dp_sum - dp[L] + MOD) % MOD;
            L++;
        }
        
        dp[i] = dp_sum;
        dp_sum = (dp_sum + dp[i]) % MOD;
    }
    
    return dp[n];
}

int main() {
    int n;
    long long k;
    cin >> n >> k;
    
    vector<long long> sightings(n);
    for (int i = 0; i < n; i++) {
        cin >> sightings[i];
    }
    
    long long result = countArrangements(n, k, sightings);
    cout << result << endl;
    
    return 0;
}
