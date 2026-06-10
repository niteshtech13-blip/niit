import java.util.*;

public class Main {

    static class DSU {
        int[] parent, rank;

        DSU(int n) {
            parent = new int[n];
            rank = new int[n];

            for (int i = 0; i < n; i++) {
                parent[i] = i;
            }
        }

        int find(int x) {
            if (parent[x] != x) {
                parent[x] = find(parent[x]);
            }
            return parent[x];
        }

        void union(int a, int b) {
            int pa = find(a);
            int pb = find(b);

            if (pa == pb) return;

            if (rank[pa] < rank[pb]) {
                parent[pa] = pb;
            } else if (rank[pa] > rank[pb]) {
                parent[pb] = pa;
            } else {
                parent[pb] = pa;
                rank[pa]++;
            }
        }
    }

    private static boolean similar(String a, String b) {
        int diff = 0;

        for (int i = 0; i < a.length(); i++) {
            if (a.charAt(i) != b.charAt(i)) {
                diff++;
                if (diff > 4) return false;
            }
        }

        return diff == 0 || diff == 2 || diff == 4;
    }

    public static int getAnagramGroups(List<String> strs) {
        int n = strs.size();
        if (n == 0) return 0;

        DSU dsu = new DSU(n);

        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if (similar(strs.get(i), strs.get(j))) {
                    dsu.union(i, j);
                }
            }
        }

        Set<Integer> groups = new HashSet<>();
        for (int i = 0; i < n; i++) {
            groups.add(dsu.find(i));
        }

        return groups.size();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        List<String> arr = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            arr.add(scanner.next());
        }

        int groups = getAnagramGroups(arr);
        System.out.println(groups);
    }
}
