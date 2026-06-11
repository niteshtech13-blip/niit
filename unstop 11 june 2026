import java.util.Scanner;

public class Main {

    public static int countValidCombos(int N, int K, int L, int R, String[] deviceTypes, int[] prices) {
        return dfs(0, 0, 0, K, L, R, prices, N);
    }

    private static int dfs(int index, int chosen, int sum,
                           int K, int L, int R, int[] prices, int N) {

        if (chosen == K) {
            return (sum >= L && sum <= R) ? 1 : 0;
        }

        if (index == N) {
            return 0;
        }

        if (chosen + (N - index) < K) {
            return 0;
        }

        int take = dfs(index + 1, chosen + 1, sum + prices[index],
                       K, L, R, prices, N);

        int skip = dfs(index + 1, chosen, sum,
                       K, L, R, prices, N);

        return take + skip;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int N = scanner.nextInt();
        int K = scanner.nextInt();
        int L = scanner.nextInt();
        int R = scanner.nextInt();

        String[] deviceTypes = new String[N];
        int[] prices = new int[N];

        for (int i = 0; i < N; i++) {
            deviceTypes[i] = scanner.next();
            prices[i] = scanner.nextInt();
        }

        int result = countValidCombos(N, K, L, R, deviceTypes, prices);
        System.out.println(result);

        scanner.close();
    }
}
