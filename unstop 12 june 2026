import java.util.*;

public class Main {

    public static List<Object> userLogic(int N, int T, List<RoomData> roomData) {
        List<Object> results = new ArrayList<>();

        for (RoomData room : roomData) {
            boolean[] required = new boolean[T];

            
            for (Interval interval : room.intervals) {
                for (int h = interval.L; h <= interval.R; h++) {
                    required[h - 1] = true; 
                }
            }

            int energyNeeded = 0;
            List<Integer> schedule = new ArrayList<>();

            for (int i = 0; i < T; i++) {
                if (required[i]) {
                    schedule.add(1); 
                    energyNeeded++;
                } else {
                    schedule.add(0); 
                }
            }

            if (energyNeeded > room.E) {
                results.add("NOT POSSIBLE");
            } else {
                results.add(schedule);
            }
        }

        return results;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int N = scanner.nextInt();
        int T = scanner.nextInt();

        List<RoomData> roomData = new ArrayList<>();

        for (int i = 0; i < N; i++) {
            int K = scanner.nextInt();
            int E = scanner.nextInt();

            List<Interval> intervals = new ArrayList<>();

            for (int j = 0; j < K; j++) {
                int L = scanner.nextInt();
                int R = scanner.nextInt();
                intervals.add(new Interval(L, R));
            }

            roomData.add(new RoomData(K, E, intervals));
        }

        List<Object> results = userLogic(N, T, roomData);

        for (Object result : results) {
            if (result instanceof String) {
                System.out.println(result);
            } else if (result instanceof List<?>) {
                List<?> schedule = (List<?>) result;

                for (int i = 0; i < schedule.size(); i++) {
                    System.out.print(schedule.get(i));
                    if (i < schedule.size() - 1) {
                        System.out.print(" ");
                    }
                }
                System.out.println();
            }
        }

        scanner.close();
    }

    static class RoomData {
        int K;
        int E;
        List<Interval> intervals;

        RoomData(int K, int E, List<Interval> intervals) {
            this.K = K;
            this.E = E;
            this.intervals = intervals;
        }
    }

    static class Interval {
        int L;
        int R;

        Interval(int L, int R) {
            this.L = L;
            this.R = R;
        }
    }
}
