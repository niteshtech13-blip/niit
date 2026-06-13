import java.util.*;

public class Main {

    public static boolean canPartitionKSubsets(int[] arr, int k) {
        int n = arr.length;

        if (k > n) return false;

        int totalSum = 0;
        for (int num : arr) {
            totalSum += num;
        }

        if (totalSum % k != 0) return false;

        int target = totalSum / k;

        Arrays.sort(arr);

        
        if (arr[n - 1] > target) return false;

        boolean[] used = new boolean[n];

        return backtrack(arr, used, k, 0, 0, target);
    }

    private static boolean backtrack(int[] arr, boolean[] used, int k,
                                     int start, int currentSum, int target) {

        
        if (k == 1) return true;

        if (currentSum == target) {
            return backtrack(arr, used, k - 1, 0, 0, target);
        }

        for (int i = start; i < arr.length; i++) {

            if (used[i]) continue;

            if (currentSum + arr[i] > target) continue;

            used[i] = true;

            if (backtrack(arr, used, k, i + 1,
                          currentSum + arr[i], target)) {
                return true;
            }

            used[i] = false;

            
            if (currentSum == 0) return false;
        }

        return false;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<Integer> data = new ArrayList<>();

        while (scanner.hasNextInt()) {
            data.add(scanner.nextInt());
        }

        int[] arr = new int[data.size() - 1];
        for (int i = 0; i < data.size() - 1; i++) {
            arr[i] = data.get(i);
        }

        int k = data.get(data.size() - 1);

        boolean result = canPartitionKSubsets(arr, k);
        System.out.println(result ? "true" : "false");
    }
}
