import java.util.*;

class ListNode {
    int val;
    ListNode next;
    ListNode(int x) { val = x; next = null; }
}

public class Main {
    public static String userLogic(ListNode head) {
        long sum=0;
        String str ="";
       while(head!=null){
        sum += head.val;
        str += head.val;
        head = head.next;
       }
       long ans = Long.parseLong(str);
       str = Long.toString(ans);
       String rev = new StringBuilder(str).reverse().toString();
       ans = Long.parseLong(rev) - sum;
        return ans%2 ==0 ? "even" : "odd" ;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        ListNode head = null;
        ListNode tail = null;
        for (int i = 0; i < N; i++) {
            int value = sc.nextInt();
            ListNode newNode = new ListNode(value);
            if (head == null) {
                head = newNode;
            } else {
                tail.next = newNode;
            }
            tail = newNode;
        }
        String result = userLogic(head);
        System.out.println(result);
    }
}
