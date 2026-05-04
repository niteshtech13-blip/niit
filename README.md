#include <string>
#include <algorithm>

using namespace std;

class Solution {
public:
    bool isBinaryPalindrome(int n) {
        string bits = "";
        while (n > 0) {
            bits += (n % 2 == 0 ? '0' : '1');
            n /= 2;
        }
        
        string reversed_bits = bits;
        reverse(reversed_bits.begin(), reversed_bits.end());
        
        return bits == reversed_bits;
    }
};
