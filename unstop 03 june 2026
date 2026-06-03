import java.io.*;
import java.util.*;

public class Main {
    public static void processDashes(int n, String s) {
        // Write your logic here.
        n = s.length();
        int count = 0;
        String res = "";
        for(int i=n-1;i>=0;i--){
            char ch = s.charAt(i);
            if(ch =='_'){
                count++;
            }
            else{
                if(count>0){
                    count--;
                    continue;
                }
                else{
                    res = ch+res;
                }
            }
        }
        if(res ==""){
            System.out.print("-1");
        }
        else{
            System.out.print(res);
        }
    }

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

    int n = Integer.parseInt(br.readLine());
    String s = br.readLine();

    processDashes(n, s);
    }
}
