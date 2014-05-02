UserInterface.java
==================
import java.util.Scanner;
import java.util.Date;
public class UserInterface 
{
    Scanner s = new Scanner(System.in);

	//Desc: Constructor for the User Interface
    public UserInterface()
	{
		int response = 0;
		while (true)
		{
			System.out.println("Please select a number"
                                + "1. Sell a Painting"
                                + "2. Buy a Painting"
                                + "3. Add/Update/Delete a File"
                                + "4. Print a Report"
                                + "5. Quit");
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
    public static void sellAPainting()
    {
        Scanner s = new Scanner(System.in);
        System.out.println("What do you want to sell? "
                + "Enter Artist Last name and painting title");
        String lname = s.nextLine();
        String title = s.nextLine();
        BoughtPainting b = findObject(lname,title);
        System.out.println(b);
        System.out.println("Confirm that this is the painting "
                + "you want to sell by entering y/n");
        String response = s.nextLine();
        if (response.matches("y"))
        {
            SoldPainting sold = new SoldPainting();
            System.out.println("Please add the name of buyer: ");
            String name = s.nextLine();
            System.out.println("Please add the address of buyer: ");
            String address = s.nextLine();
            System.out.println("Please add the actual selling price: ");
            double price = s.nextDouble();
            sold.setDate(); //add current date
            sold.setNameOfBuyer(name);
            sold.setAddressOfBuyer(address);
            sold.setActualPurchasePrice(price);
            sold.save();
        }
        if (response.matches("n")) 
            System.out.println("Painting not sold.");
        else System.out.println("Please enter character y or n");
    }
    
    //Desc: The UI for the selection Buy a Painting
    public static void buyAPainting()
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
    public static void executeDetermineMasterpiecePrice()
    {
    	Painting toBuy = getValuesFromUser();
    	if (userBuyChoice(determineMasterpiecePrice())) 
    	addRecordBoughtPaintingFile(toBuy);
    	else
    	go back to menu 
    }
    
    //Desc: prompt user to input the artist first name, last name, area of 
    //painting, title of work, date of work, medium and subject of painting user 
    //wants to buy
    //Post: The artist first name, last name, area of painting, title of 
    //work, date of work, medium and subject of painting user wants to buy have 
    //values input by the user
    public static Painting getValuesFromUser() 
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
        System.out.println("Enter painting medium: ");
    	String medium = s.nextLine();
        System.out.println("Enter painting subject: ");
    	String subject = s.nextLine();
        System.out.println("Enter painting width: ");
        String width = s.nextLine();
        System.out.println("Enter painting height: ");
        String height = s.nextLine();
        Painting buy = new Painting ();
        buy.setArtistFirstName(firstName);
        buy.setArtistLastName(lastName);
        buy.setTitleOfWork(title);
        buy.setDateOfWork(dateOfWork);
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
    public static void executeDetermineOtherWorkPrice()
    {
    	Painting toBuy = getValuesFromUser();
    	if (userBuyChoice(determineOtherWorkPrice()))
            addRecordBoughtPaintingFile(toBuy);
        //else go back to menu
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
    public static void executeDetermineMasterworkPrice()
    {
    	Painting toBuy = getValuesFromUser()
    	if (userBuyChoice(determineMasterworkPrice())
                addRecordBoughtPaintingFile(toBuy);
    	else
    	go back to menu 
    }
    


    //Desc: display a value to the user and the user responds which is returned 
    //      as a true or false value
    //Pre: the argument must be a double value
    //Return: a boolean value based on the user’s input
    public static boolean userBuyChoice(double d)
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
    public static void addRecordBoughtPaintingFile(Painting toBuy) 
    {
        Scanner s = new Scanner (System.in);
        BoughtPainting newR = toBuy;
	System.out.println ("Enter Name of Buyer: ");
	String name = s.nextLine();
	newR.setNameOfBuyer(name);
		
	System.out.println ("Enter Buyers Address: ");
	String address = s.nextLine();
	newR.setAddressOfSeller(address);

	System.out.println ("Enter Date of Purchace: ");
	String dateOfSale = s.nextLine();
	//String to date
	newR.setDateOfSale(dateOfSale);
		
 	newR.setSuggestedMaximumPurchasePrice(getSuggestedMaximumPurchasePrice());

	newR.save();
    }

    //Desc: Displays the menu for adding, updating or deleting files
    public static void changeFiles()
    {  
       Scanner s = new Scanner (System.in);
       print("Which file would you like to change?"
               + "1. ArtistFile (update add or delete) call boundary class"
               + "2. PaintingsSold");
        int response = s.nextInt();
        if(response ==1)updateArtistFile();
        if(response ==2)updatePaintingFile();

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
        if(response ==1)
            ProduccePaintingsPurchasedInThePastYearReport.printReport();
        if(response==2)
            ProducePaintingsSoldInThePastYearReport.printReport();
        if(response==3)
            ProducePaintingsExceedingTargetSellingPrice.printReport();
    }
}
