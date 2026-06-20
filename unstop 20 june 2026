import java.util.*;

public class Main {

    public static int maxChocolates(int[][] grid, int n, int m) {

        int[][] front = new int[m][m];

        for (int c1 = 0; c1 < m; c1++) {
            for (int c2 = 0; c2 < m; c2++) {
                if (c1 == c2)
                    front[c1][c2] = grid[n - 1][c1];
                else
                    front[c1][c2] = grid[n - 1][c1] + grid[n - 1][c2];
            }
        }

        for (int row = n - 2; row >= 0; row--) {
            int[][] curr = new int[m][m];

            for (int c1 = 0; c1 < m; c1++) {
                for (int c2 = 0; c2 < m; c2++) {

                    int best = Integer.MIN_VALUE;

                    for (int d1 = -1; d1 <= 1; d1++) {
                        for (int d2 = -1; d2 <= 1; d2++) {

                            int nc1 = c1 + d1;
                            int nc2 = c2 + d2;

                            if (nc1 < 0 || nc1 >= m || nc2 < 0 || nc2 >= m)
                                continue;

                            int value;
                            if (c1 == c2)
                                value = grid[row][c1];
                            else
                                value = grid[row][c1] + grid[row][c2];

                            value += front[nc1][nc2];

                            best = Math.max(best, value);
                        }
                    }

                    curr[c1][c2] = best;
                }
            }

            front = curr;
        }

        return front[0][m - 1];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        int[][] grid = new int[n][m];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                grid[i][j] = scanner.nextInt();
            }
        }

        System.out.println(maxChocolates(grid, n, m));
    }
}
