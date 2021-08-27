
#Coditation Assignment

import java.util.Scanner;
class Operation {
    public void LiveorDead(int[][] board) {
        
    int [][] board2 = new int[board.length][board[0].length];  
        
           
        for(int i  = 0; i < board.length; i++)
            for(int j = 0;j < board[0].length; j++)
                {
                board2[i][j] = check(i,j,board);
                }
        
        
          
        for(int i  = 0; i < board.length; i++)
            for(int j = 0;j < board[0].length; j++)
                {
                board[i][j] = board2[i][j];
                }
        
        return;
    }
          
    
    public int check(int i, int j, int [][] board)
        {
            if(board[i][j] == 1  && count(i,j,board) < 2 )  return 0;
            else if (board[i][j] == 1 && (count(i, j, board) == 2 || count(i, j, board) == 3)) return 1;
            else if (board[i][j] == 1 && count(i, j, board) > 3) return 0;
            else if (board[i][j] == 0 && count(i, j, board) == 3) return 1; 
        return 0;
        }
   
        
    public int count(int i, int j, int[][] board)
        {
        int counter = 0;   
        for(int k = 0; k<3; k++)
                for(int l = 0; l<3;l++)
                    {
                    if(k == 1 && l == 1) continue;
                    counter += isAlive(i + k - 1, j + l - 1, board);
                    }
            return counter;
        }
    
          
    public int isAlive(int k, int l, int [][] board)
        {
                if (k > board.length -1|| k < 0 || l > board[0].length -1 || l < 0) return 0;
                else return board[k][l];
        }
    
}
public class Main
{
	public static void main(String[] args) {
		
		Scanner sc=new Scanner(System.in);
		
		System.out.println("Enter no.of rows in the grid");
		
		int n=sc.nextInt();
		
		System.out.println("Enter no.of columns in the grid");
		
		int m=sc.nextInt();
		
		int grid[][]=new int[n][m];
		
		System.out.println("Enter elements of grid. press 1 if cell is alive || press 0 if cell is dead");
		System.out.println();
		
		    for(int i=0;i<n;i++){
		        for(int j=0;j<m;j++){
		            grid[i][j]=sc.nextInt();
		        }   
	        }
	    
	      System.out.println();
	      System.out.println("Future :");
	      System.out.println();
	    
	    
	    Operation ob=new Operation();
	    
	    ob.LiveorDead(grid);
	    
	        for(int i=0;i<n;i++){
		        for(int j=0;j<m;j++){
		            System.out.print(grid[i][j]+" ");
		 }
		System.out.println();
	    }
	}
}
