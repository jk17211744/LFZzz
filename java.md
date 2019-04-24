# java树状数组（我的第一个java程序）
```
import java.util.*;
import java.math.*;
public class Main {
        static int []res = new int[2100];
         
        public static int lowbit (int n)
        {
            return n & -n;
        }
         
        public static void Update(int n)
        {
            while(n < 2100)
            {
                res[n]++;
                n += lowbit(n);
            }
        }
         
        public static int Getsum(int n)
        {
            int ans = 0;
            while(n >= 1)
            {
                ans += res[n];
                n -= lowbit(n);
            }
            return ans;
        }
         
        public static void main(String[] args) {
             Scanner cin = new Scanner(System.in);
                 while(cin.hasNext())
                 {
                     int ans = 0;
                     for(int i = 0;i < 2100;i++)
                         res[i] = 0;
                     String a = cin.nextLine();
                     for(int i = 0;i < a.length();i++)
                     {
                         Update((int)a.charAt(i));
                         ans += (i + 1 - Getsum((int)a.charAt(i)));
                     }
                     System.out.println(ans);
                 }
         }  
}
 
 ```
