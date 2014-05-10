import java.io.DataInputStream;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Date;
import java.util.Scanner;
public class UserInterface 
{
    Scanner s = new Scanner(System.in);

	//Desc: Constructor for the User Interface
    public UserInterface()
	{
		int response = 0;
		while (true)
                {
		
                        System.out.println ("\t             WELCOME -- MAIN MENU\n\n");
			System.out.println ("\t         Oglesby Art Pricing System\n\n");
			System.out.println("\t      Please select a number\n"
                                + "\t       1. Sell a Painting\n"
                                + "\t       2. Buy a Painting\n"
                                + "\t       3. Add/Update/Delete a File\n"
                                + "\t       4. Print a Report\n"
                                + "\t       5. Quit\n");
			response = s.nextInt();
			if(response == 5) break;
			if(response == 1) UpdateSoldPaintingsFile.addSoldPaintingFile();
			if(response == 2) buyAPainting();
			if (response == 3) changeFiles();
			if (response == 4) printReport();
		}
		System.out.println("Program completed");
	}
    
    //Desc: The UI for the selection Buy a Painting
    public static void buyAPainting() //keep
    {
        Scanner s = new Scanner(System.in);
        while (true)  
        {   
            clearScreen();
            int response = 0;
            System.out.println ("\t             BUY A PAINTING\n\n");
            System.out.println ("\t         Oglesby Art Pricing System\n\n");
            System.out.println ("\t     What type of painting do you want to buy?\n"
                    + "\t       1. Masterpiece\n"
                    + "\t       2. Masterwork\n"
                    + "\t       3. Other work\n"
                    + "\t       Enter number 1, 2 or 3");
            response = s.nextInt();
           // if(response == 1) executeDetermineMasterpiecePrice();
            //if(response == 2) executeDetermineMasterworkPrice();
            //if (response == 3) executeDetermineOtherWorkPrice();
            //else System.out.println("Please enter a number 1, 2 or 3");
        }
        
    }

    
   

    //Desc: Displays the menu for adding, updating or deleting files
    public static void changeFiles()
    {
        clearScreen();
        Scanner s = new Scanner (System.in);
        System.out.println ("\t             CHANGE A FILE\n\n");
        System.out.println ("\t         Oglesby Art Pricing System\n\n");
        System.out.println("\t      Which file would you like to change?\n"
               + "\t        1. ArtistFile\n"
               + "\t        2. PaintingsSold");
        int response = s.nextInt();
        if(response ==1) UpdateArtistFile.updateArtistFile();
        if(response ==2) UpdateSoldPaintingsFile.addSoldPaintingFile();

    }
    //Desc: Displays the menu for different reports
    public static void printReport()
    {
        clearScreen();
        Scanner s = new Scanner (System.in);
        System.out.println ("\t             PRINT A REPORT\n\n");
        System.out.println ("\t         Oglesby Art Pricing System\n\n");
        System.out.println("\t      Which report would you like to print? \n"
                + "\t       1. Paintings Purchased In The Past Year Report\n"
                + "\t       2. Paintings Sold In The Past Year Report\n"
                + "\t       3. Paintings Exceeding Target Selling Price Report\n"
                + "\t       Please enter a number 1, 2 or 3.");
        int response = 0;
        response = s.nextInt();
       /* if(response ==1)
            ProduccePaintingsPurchasedInThePastYearReport.printReport();
        if(response==2)
            ProducePaintingsSoldInThePastYearReport.printReport();
        if(response==3)
            ProducePaintingsExceedingTargetSellingPrice.printReport();**/
    }
    
      public static char getChar()
  //
  // the following method returns the first character entered on the keyboard
  //
  {

     char ch = '\n';

     try
     {

        InputStreamReader in = new InputStreamReader(System.in);
        ch = (char)in.read();

     }
     catch (Exception e)
     {

        System.out.println("Error: " + e.toString());

     }

     return ch;

  }  // getChar

//----------------------------------------------------------------------------------------------------------------------------------------------------

  public static int getInt()
  //
  // the following method returns an integer entered from the keyboard
  //
  {

     int res;
     String strInt;

     strInt = getString();
     res = (short)Integer.parseInt(strInt);

     return res;

  } // getInt
  
  
    public static double getDouble()
  //
  // the following method returns a double entered from the keyboard
  //
  {

     double res;
     String strDouble;

     strDouble = getString();
     res = Double.parseDouble(strDouble);

     return res;

  } // getInt

//----------------------------------------------------------------------------------------------------------------------------------------------------

  public static String getString()
  //
  // the following method returns a string entered from the keyboard
  //
  {
     String str = "_";

     try
     {

        DataInputStream MyInput = new DataInputStream(System.in);
        str = MyInput.readLine();

     }
     catch (Exception e)
     {

        System.out.println("Error: " + e.toString());

     }

     return str;

  }  // getString
  public static void clearScreen ()
  //
  // clearScreen clears the screen
  //
  {
    int	i;		// loop counter representing the number of blank lines to be printed

    //
    // Implementation-dependent code to clear the screen should replace the code
    // given below.
    //
    for (i = 0; i < 26; i++)
    {
	System.out.println ();
    }

  }  // clearScreen ()
  
    public static void pressEnter()
  //
  // press_enter waits until the user presses the <enter> key
  //
  {
     try
     {

       DataInputStream MyInput = new DataInputStream(System.in);
       String inputLine = MyInput.readLine();

     }
     catch (IOException e)
     {

       System.out.println("I/O exeption");

     }

  }
  
}
