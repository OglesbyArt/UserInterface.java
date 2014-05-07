UserInterface.java
==================
import java.io.DataInputStream;
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
			System.out.println("Please select a number\n"
                                + "1. Sell a Painting\n"
                                + "2. Buy a Painting\n"
                                + "3. Add/Update/Delete a File\n"
                                + "4. Print a Report\n"
                                + "5. Quit\n");
			response = s.nextInt();
			if(response == 5) break;
			if(response == 1) sellAPainting();
			if(response == 2) buyAPainting();
			if (response == 3) changeFiles();
			if (response == 4) printReport();
		}
		System.out.println("Program completed");
	}

    //Desc: Prints the menu for sell a painting
    public static void sellAPainting() //not keep
    {
        Scanner s = new Scanner(System.in);
        System.out.println("What do you want to sell? "
                + "Enter Artist Last name and painting title");
        String lname = s.nextLine();
        String title = s.nextLine();
        BoughtPainting b = new BoughtPainting(); //this doesn't do anything
        System.out.println(b);
        System.out.println("Confirm that this is the painting "
                + "you want to sell by entering y/n");
        String response = s.nextLine();
        if (response.matches("y"))
        {

        }
        if (response.matches("n")) 
            System.out.println("Painting not sold.");
        else System.out.println("Please enter character y or n");
    }
    
    //Desc: The UI for the selection Buy a Painting
    public static void buyAPainting() //keep
    {
        Scanner s = new Scanner(System.in);
        while (true)
        {   int response = 0;
            System.out.println ("What type of painting do you want to buy?"
                    + "1. Masterpiece"
                    + "2. Masterwork"
                    + "3. Other work"
                    + "Enter number 1, 2 or 3");
            response = s.nextInt();
            if(response == 1) executeDetermineMasterpiecePrice();
            if(response == 2) executeDetermineMasterworkPrice();
            if (response == 3) executeDetermineOtherWorkPrice();
            else System.out.println("Please enter a number 1, 2 or 3");
        }
        
    }


    //Desc: Executes the major methods that allow a user to buy a painting. 
    // First the user must input values, then the user will view the 
    //suggested price. If the user chooses by buy then the bought painting file
    //will be updated, otherwise the user can go back to the main
    //menu
    //Pre: There must be a coefficient of similarity, otherwise
    //the user is not interested in buying the painting. 
    //Post: The user will have viewed the suggested maximum price for 
    //the painting they want to buy. If they chose to buy it, the files are 
    //now updated accordingingly. 
    public static void executeDetermineMasterpiecePrice() //dont keep
    {

    }
    
    //Desc: prompt user to input the artist first name, last name, area of 
    //painting, title of work, date of work, medium and subject of painting user 
    //wants to buy
    //Post: The artist first name, last name, area of painting, title of 
    //work, date of work, medium and subject of painting user wants to buy have 
    //values input by the user
    public static BoughtPainting getValuesFromUser() //dont keep
    {
    	Scanner s = new Scanner (System.in);
        System.out.println("Enter Artist First name: ");
    	String firstName = s.nextLine();
        System.out.println("Enter Artist Last name: ");
    	String lastName = s.nextLine();
        System.out.println("Enter title of painting: ");
    	String title = s.nextLine();
        System.out.println("Enter date painting was created: ");
    	String dateOfWork = s.nextLine();
        Date date = new Date(dateOfWork);
        System.out.println("Enter painting medium: ");
    	String medium = s.nextLine();
        System.out.println("Enter painting subject: ");
    	String subject = s.nextLine();
        System.out.println("Enter painting width: ");
        String w = s.nextLine();
        Double width = new Double(w);
        System.out.println("Enter painting height: ");
        String h = s.nextLine();
        Double height = new Double(h);
        BoughtPainting buy = new BoughtPainting ();
        buy.setArtistFirstName(firstName);
        buy.setArtistsLastName(lastName);
        buy.setTitleOfWork(title);
        buy.setDateofWork(date);
        buy.setMedium(medium);
        buy.setSubject(subject);
        buy.setWidth(width);
        buy.setHeight(height);
        return buy;
    }


    //Desc: Executes the major methods that allow a user to buy a painting. 
    // First the user must input values, then the user will view the 
    //suggested price. If the user chooses by buy then the bought painting file
    //will be updated, otherwise the user can go back to the main
    //menu
    //Pre: The Fashionability Value must not be zero for that arist, otherwise
    //the user is not interested in buying the painting. 
    //Post: The user will have viewed the suggested maximum price for 
    //the painting they want to buy. If they chose to buy it, the files are 
    //now updated accordingingly. 
    public static void executeDetermineOtherWorkPrice() //dont keep
    {

    }


    //Desc: Executes the major methods that allow a user to buy a painting. 
    // First the user must input values, then the user will view the 
    //suggested price. If the user chooses by buy then the bought painting file
    //will be updated, otherwise the user can go back to the main
    //menu
    //Pre: The coefficient of similarity must not be zero, otherwise
    //the user is not interested in buying the painting. 
    //Post: The user will have viewed the suggested maximum price for 
    //the painting they want to buy. If they chose to buy it, the files are 
    //now updated accordingingly. 
    public static void executeDetermineMasterworkPrice() //dont keep
    {

    }
    


    //Desc: display a value to the user and the user responds which is returned 
    //      as a true or false value
    //Pre: the argument must be a double value
    //Return: a boolean value based on the user’s input
    public static boolean userBuyChoice(double d) //dont keep
    {
    	System.out.println("The price is" +d +". Do you want to buy? y/n");
    	Scanner s = new Scanner(System.in);
        String response = s.nextLine();
        //must do error checking
        if (response.matches("y")) return true;
        else return false;
    }


    //Desc: updates the bought painting file by adding a new record for the 
    //current painting that the user just bought
    //Pre: the BoughtPainting.txt file must exist
    //Post: The bought paintings file is updated
    public static void addRecordBoughtPaintingFile(Painting toBuy) //dont keep
    {

    }

    //Desc: Displays the menu for adding, updating or deleting files
    public static void changeFiles()
    {  
       Scanner s = new Scanner (System.in);
       System.out.println("Which file would you like to change?"
               + "1. ArtistFile"
               + "2. PaintingsSold");
        int response = s.nextInt();
        if(response ==1)
        {
            System.out.println("What do you want to change/n"
                    + "1. Artist first name/n"
                    + "2. Artist last name/n"
                    + "3. Artist Fashionability Value");
            response = s.nextInt();
            //if(response ==1) Artist.updateArtistsFirstName();
        }
        if(response ==2)
        {
            System.out.println("What do you want to change/n"
                    + "1. Artist first name/n"
                    + "2. Artist last name/n"
                    + "3. Title of Work /n"
                    + "4. Classification/n"
                    + "5. Date of Work/n"
                    + "6. Height/n"
                    + "7. Width/n"
                    + "8. Medium/n"
                    + "9. Subject/n"
                    + "10. Suggested Maximum Purchase Price");
            response = s.nextInt();
            //if (response ==1) Painting.updateArtistsFirstName();
        }

    }
    //Desc: Displays the menu for different reports
    public static void printReport()
    {
        Scanner s = new Scanner (System.in);
        System.out.println("Which report would you like to print? "
                + "1. Paintings Purchased In The Past Year Report"
                + "2. Paintings Sold In The Past Year Report"
                + "3. Paintings Exceeding Target Selling Price Report"
                + "Please enter a number 1, 2 or 3.");
        int response = 0;
        response = s.nextInt();
       /* if(response ==1)
            ProduccePaintingsPurchasedInThePastYearReport.printReport();
        if(response==2)
            ProducePaintingsSoldInThePastYearReport.printReport();
        if(response==3)
            ProducePaintingsExceedingTargetSellingPrice.printReport();**/
    }
    public static void main (String[] args)
    {
        UserInterface h = new UserInterface();
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
  
}
