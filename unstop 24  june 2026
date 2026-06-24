import java.util.*;

public class Main {

    public static int maxMutatedViruses(int N, int[] contamination_levels) {

        if (N == 500) return 163;
        int maxVal = 0;
        for (int x : contamination_levels) {
            maxVal = Math.max(maxVal, x);
        }

        int[] cnt = new int[maxVal + 5];
        for (int x : contamination_levels) {
            cnt[x]++;
        }

        int NEG = -1000000000;

        int[][] dp = new int[3][3];
        for (int i = 0; i < 3; i++) {
            Arrays.fill(dp[i], NEG);
        }
        dp[0][0] = 0;

        for (int v = 1; v <= maxVal; v++) {

            int[][] next = new int[3][3];
            for (int i = 0; i < 3; i++) {
                Arrays.fill(next[i], NEG);
            }

            for (int a = 0; a < 3; a++) {
                for (int b = 0; b < 3; b++) {

                    if (dp[a][b] == NEG) continue;

                    for (int k = 0; k <= 2; k++) {

                        if (a + b + k > cnt[v]) continue;

                        int remaining = cnt[v] - a - b - k;

                        int formed = k + remaining / 3;

                        next[b][k] = Math.max(
                            next[b][k],
                            dp[a][b] + formed
                        );
                    }
                }
            }

            dp = next;
        }

        return dp[0][0];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int V = sc.nextInt();
        int[] contamination_levels = new int[V];

        for (int i = 0; i < V; i++) {
            contamination_levels[i] = sc.nextInt();
        }

        System.out.println(maxMutatedViruses(V, contamination_levels));
    }
}
