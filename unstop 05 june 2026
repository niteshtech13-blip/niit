import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        
        user_logic(n, nums);
    }
    
    static void user_logic(int n, int[] nums) {
        // Write your logic here.
        int sum = (int)Math.pow(2,nums[0]);
        for(int i=1;i<n;i++){
            if(nums[i] != nums[i-1]){
                sum += (int)Math.pow(2,nums[i]);
            }
        }
        System.out.print(sum);
    }
}
