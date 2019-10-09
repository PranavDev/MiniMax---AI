import java.io.*;
import java.util.*;

public class MiniMax_XO
{
	//State Structure
	public static class NodeState
	{
		public String GameArray[];
		public int Level;
		public int BestValue;
		public NodeState parent;
		public NodeState child;
		public NodeState sibling;
		
		public NodeState(String GameArray[], int Level, int BestValue, NodeState parent, NodeState child, NodeState sibling)
		{
			this.GameArray = GameArray;
			this.Level = Level;
			this.BestValue = BestValue;
			this.parent = parent;
			this.child = child;
			this.sibling = sibling;
		}
		
	}
	
	
	
	//Declarations
	
	public static String InitState[] = new String[9];
	public static String NewState[] = new String[9];
	public static int Next_Move_Positions[] = new int[9];
	public static Scanner sc = new Scanner(System.in);
	public static String Whose_Turn = "";
	public static Random rand = new Random();
	public static int CutOff_Level = 0;
	public static int Player_Mode = 0;
	public static int Rem_Moves = 0;
	
	
	
	//Display Node
	public static void displayState(NodeState Node)
	{
		int j = 0, i = 0;

		while(i<9)
		{
			while(j<3)
			{
				System.out.print(Node.GameArray[i]+" ");
				j++;
				i++;
			}
			j = 0;
			System.out.println("\n");
		}
		System.out.println("State Level : "+Node.Level);
		System.out.println("Parent : "+Node.parent);
		System.out.println("Child : "+Node.child);
		System.out.println("Sibling : "+Node.sibling);
	}
	
	
	
	
	public static void display(String Array[])
	{
		int j = 0, i = 0;

		while(i<9)
		{
			while(j<3)
			{
				System.out.print(Array[i]+" ");
				j++;
				i++;
			}
			j = 0;
			System.out.println("\n");
		}
	}
	
	
	
	//Checks Next Turn
	public static String Check_Whose_Turn(String State[])
	{
		int X_moves = 0,O_moves = 0;
		for(int i=0;i<9;i++)
		{
			if(State[i].equalsIgnoreCase("X"))
			{
				X_moves++;
			}
			else if(State[i].equalsIgnoreCase("O"))
			{
				O_moves++;
			}
		}
		
		if(X_moves > O_moves)
		{
			return("O");
		}
		else if(O_moves > X_moves)
		{
			return("X");
		}
		else
		{
			int r = rand.nextInt(10);
			if(r%2==0)
			{
				return("O");
			}
			else
			{
				return("X");
			}
		}
	}
	
	
	
	
	//calculates the no. of empty spaces in the GameArray for moves
	public static int Moves = 0;
	public static int Available_Moves(String State[])
	{
		Moves = 0;
		for(int i=0;i<9;i++)
		{
			if(State[i].equalsIgnoreCase("-"))
			{
				Moves++;
			}
		}
		return Moves;
	}
	
	
	
	
	
	//gets the index positions of blank spaces in the GameArray for next move
	public static int INDX = 0;
	public static void Get_Free_Move_Positions(String Array[])
	{
		for(int i=0;i<9;i++)
		{
			if(Array[i].equalsIgnoreCase("-"))
			{
				Next_Move_Positions[INDX] = i;
				INDX++;
			}
		}
	}
	
	
	
	
	public static String[] Play_Next_Move(String Array[],int Pos,String s)
	{
		Array[Pos] = s;
		return(Array);
	}
	
	
	
	public static String[] Forget_Move(String Array[],int Pos)
	{
		Array[Pos] = "-";
		return(Array);
	}
	
	
	
	
	//MiniMax Function
	public static void MiniMax(NodeState Node,int Depth,int Mode)
	{	
		if(Depth!=0)
		{
			Rem_Moves = Available_Moves(Node.GameArray);
			System.out.println("Empty Spaces for Game Play : "+Rem_Moves);
			
			
			//Gets the Next Turn : If X or O
			Whose_Turn = Check_Whose_Turn(Node.GameArray);
			System.out.println("Next Turn : "+Whose_Turn+"\n\n");
			
			
			//Get Index Positions of Free Spaces in the GameArray
			Get_Free_Move_Positions(Node.GameArray);
			System.out.print("\n-> Next Move Positions : ");
			for(int i=0;i<INDX;i++)
			{
				System.out.print(Next_Move_Positions[i]+",");
			}
			
			
			//O's Turn
			if(Whose_Turn.equalsIgnoreCase("O"))
			{
				//Maximizing Player 1.Maximize 2.Minimize
				if(Mode==1)
				{
					for(int i=0;i<Rem_Moves;i++)
					{
						//NodeState Temp = new NodeState();
						
						//Temp.GameArray = Play_Next_Move(Node,Next_Move_Positions[i],Whose_Turn);
					}
					
					Mode = 0;
				}
				else
				{
					
					
					Mode = 1;
				}
			}
			
			//X's Turn
			else if(Whose_Turn.equalsIgnoreCase("X"))
			{
				//Maximizing Player 1.Maximize 2.Minimize
				if(Mode==1)
				{
					
					
					Mode = 0;
				}
				else
				{
					
					
					Mode = 1;
				}
			}
		}
		else
		{
			
		}
		
		Depth--;
	}
	
	
	
	
	//Main Declarations and Main Function
	public static void main(String args[])throws IOException
	{
		System.out.println("***********MINIMAX : TIC TAC TOE***********\n\n");
		
		//Initialize and Get the Current State : Root Node
		System.out.println("----Enter the Root Node----\n");
		System.out.print("\nEnter the Level : ");
		int lvl = sc.nextInt();
		
		System.out.println("\nEnter the GameArray : ");
		for(int i=0;i<9;i++)
		{
			System.out.println("-> Position "+(i+1)+" : ");
			InitState[i] = sc.next();
		}
		NodeState Root = new NodeState(InitState,lvl,9999,null,null,null);
		NodeState Parent = Root;
		NodeState ptr = Root;
		
		
		System.out.println("\n\n----Entered Initial State----\n");
		displayState(Root);
		
		
		
		
		//Gets Player Type
		System.out.print("\n\n-> ENTER 1.MAXIMIZE OR 2.MINIMIZE : ");
		Player_Mode = sc.nextInt();
		
		
		
		//Gets Levels
		System.out.print("\n-> Enter the Cut-off Level : ");
		CutOff_Level = sc.nextInt();
		
		
		
		Rem_Moves = Available_Moves(Root.GameArray);
		System.out.println("\n\nEmpty Spaces for Game Play : "+Rem_Moves);
		
		
		//Gets the Next Turn : If X or O
		Whose_Turn = Check_Whose_Turn(Root.GameArray);
		System.out.println("Next Turn : "+Whose_Turn+"\n\n");
		
		
		Get_Free_Move_Positions(Root.GameArray);
		System.out.print("\n-> Next Move Positions : ");
		for(int i=0;i<INDX;i++)
		{
			System.out.print(Next_Move_Positions[i]+",");
		}
		for(int i=0;i<Rem_Moves;i++)
		{
			System.out.println("\n\n------------------------------\n");
			System.out.println("---> Parent Node "+(i+1)+" \n");
			displayState(Parent);
			
			NewState = Parent.GameArray;
			NewState = Play_Next_Move(NewState,Next_Move_Positions[i],Whose_Turn);
			
			NodeState Temp = new NodeState(NewState,1,9999,Parent,null,null);
			
			if(i==0)
			{
				Parent.child = Temp;
				ptr = Temp;
			}
			if(i>0)
			{
				ptr.sibling = Temp;
				ptr = ptr.sibling;
			}
			
			System.out.println("\n---> Created Node "+(i+1)+" \n");
			displayState(Temp);
			
			//InitState = Forget_Move(NewState,Next_Move_Positions[i]);
		}
		
		System.out.println("\n\n############################################\n");
		ptr = Root;
		while(ptr!=null)
		{
			if(ptr.Level==0)
			{
				displayState(ptr);
				ptr = ptr.child;
			}
			else
			{
				displayState(ptr);
				ptr = ptr.sibling;
			}
		}
		
		//Calling the MiniMax
		//MiniMax(Root_GameState,CutOff_Level,Player_Mode);
	}
}
