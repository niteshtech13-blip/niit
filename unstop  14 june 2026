import java.util.*;

class Main {
    public static void userLogic(int n, String s) {
        Character[] arr = new Character[n];

        for (int i = 0; i < n; i++) {
            arr[i] = s.charAt(i);
        }

        Arrays.sort(arr, (c1, c2) -> {
            int diff1 = (c1 - 'a' + 1) % 5;
            int diff2 = (c2 - 'a' + 1) % 5;

            if (diff1 != diff2) {
                return diff1 - diff2;
            }

            return c2 - c1; 
        });

        StringBuilder sb = new StringBuilder();
        for (char ch : arr) {
            sb.append(ch);
        }

        System.out.println(sb.toString());
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        String s = scanner.next();

        userLogic(n, s);
    }
}
