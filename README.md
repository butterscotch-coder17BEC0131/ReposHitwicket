# ReposHitwicket
hitwicket exam repo
import java.util.*; 
public class PawnGame {

	public static void main(String[] args) {
		
		String [][] board = new String[5][5];
		
		// create an empty board. 
		
		for(int i=0 ; i <5 ; i++)
		{
			for(int j =0 ; j<5 ; j++)
			{
				board[i][j] = "-";
			}
		}
		
        // for the first move from player A
		int[] AFirstMove = new int[5]; 
		AFirstMove = firstInputNumbers(5,5);
				
		// add A's elements and their positions to the HashMap
		HashMap<String, int[] > LifeA = new HashMap<>(); 
		
		for(int i=0 ; i < 5 ; i++)
		{
			board[4][i] = "A-P"+ Integer.toString(AFirstMove[i]) ; 
			int[] pos = new int[2];
			pos[0] = 4; 
			pos[1] = i ;
			LifeA.put(Integer.toString(AFirstMove[i]), pos);
		}
		
		// print the board after A first move. 
		
		for(int i=0 ; i <5 ; i++)
		{
			for(int j =0 ; j<5 ; j++)
			{
				System.out.print(board[i][j]+"    ");
			}
			System.out.println();
		}
		
		
		
		System.out.println();
		System.out.println();
		System.out.println();
		System.out.println();
		System.out.println();
		
		// for the first move from player B
		
		
		int[] BFirstMove = new int[5]; 
		BFirstMove = firstInputNumbers(5,5);
		// add A's elements and their positions to the HashMap
		HashMap<String, int[] > LifeB = new HashMap<>(); 
		
		for(int i=0 ; i < 5 ; i++)
		{
			board[0][i] = "B-P"+ Integer.toString(BFirstMove[i]) ; 
			int[] pos = new int[2];
			pos[0] = 0; 
			pos[1] = i ;
			LifeB.put(Integer.toString(BFirstMove[i]), pos);
			
		}
		
		// print the board after B first move. 
		
		for(int i=0 ; i <5 ; i++)
		{
			for(int j =0 ; j<5 ; j++)
			{
				System.out.print(board[i][j]+"    ");
			}
			System.out.println();
		}
		
		// keep playing  until either of the player's all pawns are dead. 
		int chance = 1; // if odd, it's A chance, else B's. 
		Scanner sc = new Scanner(System.in);
		while((!LifeA.isEmpty()) && (!LifeB.isEmpty()) == true) {
			
			if(chance%2 != 0)
			{
				String AMove = sc.nextLine(); 
				int PawnNum = (int) AMove.charAt(1);
				// moves are something like  P4:F
				char PawnMove = AMove.charAt(3);
				if(LifeA.containsKey(PawnNum))
				{
					// if the pawn is alive 
					 if(ResMoveCheck('A',PawnNum,PawnMove, LifeA.get(PawnNum),board)==true)
					 {
						 ResMove('A',PawnNum, PawnMove, LifeA.get(PawnNum), board);
						  chance ++; 
					 }
					 else 
					 {
						 // take input again; 
					 }
					
				}
				
			}
			
		}
		

	}
	
	public static boolean ResMoveCheck(char player , int PawnNum , char PawnMove, int[] PawnPos, String[][] board)
	{
		// if pawns of the same player are present  - return false ; 
		// else if - if the after the movement, the pawn goes out of the board in any of the
		     // four sides - return false ; 
		// else return true; - the movement is valid 
		return true ; 
	}
	public static void ResMove(char player, int PawnNum , char PawnMove , String[][] board )
	{
		// since the given movement is valid, 
		/* if (there is given movement invloves killing other player)
		{
		
		 Step 1 : check which pawn of the other player is present there and remove that player 
		 from LifeB hashMap 
		 Step 2 : Update the position of the current pawn - the one that killed the other side's 
		 pawn in LifeA hashMap ; 
		 Step 3 : Update the position of current pawn in the board. 
			
		}*/
	}
	
	public static final Random gen = new Random();  
	public static int[] firstInputNumbers(int n, int maxRange) {  
	    assert n <= maxRange : "cannot get more unique numbers than the size of the range";  
	      
	    int[] result = new int[n];  
	    Set<Integer> used = new HashSet<Integer>();  
	    used.add(0);
	      
	    for (int i = 0; i < n; i++) {  
	          
	        int newRandom;  
	        do {  
	            newRandom = gen.nextInt(maxRange+1);  
	        } while (used.contains(newRandom));  
	        result[i] = newRandom;  
	        used.add(newRandom);  
	    }  
	    return result;  
	}  
	
	

}
