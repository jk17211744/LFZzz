# LFZzz
## B - Tempter of the Bone

### Description
The doggie found a bone in an ancient maze, which fascinated him a lot. However, when he picked it up, the maze began to shake, and the doggie could feel the ground sinking. He realized that the bone was a trap, and he tried desperately to get out of this maze. 

The maze was a rectangle with sizes N by M. There was a door in the maze. At the beginning, the door was closed and it would open at the T-th second for a short period of time (less than 1 second). Therefore the doggie had to arrive at the door on exactly the T-th second. In every second, he could move one block to one of the upper, lower, left and right neighboring blocks. Once he entered a block, the ground of this block would start to sink and disappear in the next second. He could not stay at one block for more than one second, nor could he move into a visited block. Can the poor doggie survive? Please help him. 
### Input
The input consists of multiple test cases. The first line of each test case contains three integers N, M, and T (1 < N, M < 7; 0 < T < 50), which denote the sizes of the maze and the time at which the door will open, respectively. The next N lines give the maze layout, with each line containing M characters. A character is one of the following: 

'X': a block of wall, which the doggie cannot enter; 
'S': the start point of the doggie; 
'D': the Door; or 
'.': an empty block. 

The input is terminated with three 0's. This test case is not to be processed. 
### Output
For each test case, print in one line "YES" if the doggie can survive, or "NO" otherwise. 
### Sample Input
4 4 5

S.X.

..X.

..XD

....

3 4 5

S.X.

..X.

...D

0 0 0 
### Sample Output
NO

YES 

```
import java.util.*;
import java.math.*;
public class Main {
	    static char [][]Map = new char[10][10];
	    static int n,m,k,begin_x,begin_y,end_x,end_y;
	    static int [][]f = {{-1,0},{1,0},{0,-1},{0,1}};
	    static boolean falg = false; 
	    
	    static boolean solve(int x,int y, int t)
	    {
	    	if(x >= 0 && y >= 0 && x < n && y < m && Map[x][y] != 'X' && t <= k)
	    		return true;
	    	return false;
	    }
	    
	    static void Dfs(int x,int y,int t)
	    {
	    	if(x == end_x && y ==end_y && t == k)
	    	{
	    		falg = true;
	    		return ;
	    	}
	    	if(k % 2 != (begin_x + begin_y + end_x + end_y) % 2 || falg == true)
	    		return ;
	    	Map[x][y] = 'X';
	    	for(int []res : f)
	    		if(solve(x + res[0],y + res[1],t + 1) == true)
	    			Dfs(x + res[0],y + res[1],t + 1);
	    	Map[x][y] = '.';
	    	return ;
	    }
	    
		public static void main(String[] args) {
			 Scanner cin = new Scanner(System.in);
				 while(cin.hasNext())
				 {
					 falg = false;
					 n = cin.nextInt();
				 	 m = cin.nextInt();
					 k = cin.nextInt();
					 if(n == 0 && m == 0 && k == 0)
						 break;
					 for(int i =0;i < n;i++)
					 {
						 String res = cin.next();
						 for(int j = 0;j < m;j++)
						 {
							 Map[i][j] = res.charAt(j);
							 if(Map[i][j] == 'S')
							 {
								 begin_x = i;
								 begin_y = j;
							 }
							 if(Map[i][j] == 'D')
							 {
								 end_x = i;
								 end_y = j;
							 }
						 }
					 }
					 Dfs(begin_x,begin_y,0);
					 if(falg == true)
						 System.out.println("YES");
					 else
						 System.out.println("NO");
				}
		 }	
}
```
