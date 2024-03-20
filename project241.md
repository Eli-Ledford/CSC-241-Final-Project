// CSC-241-Final-Project 
import java.util.*;

/*
* Author: Eli Ledford, Murtazza and Venessa
* Date: 03/12/2024
* Purpose: 
*/
public class project241 {
	public static void main(String[] args) {
		//declare scanner object
		Scanner scnr = new Scanner(System.in);
		
		//declare object
		EmployeeInfo[] Employee = new EmployeeInfo[3]; 
		
		//declare variables
		String employeeEmail;
		String employeeID;
		String employeeName;
		int employeeRating = 0;
		boolean isValid;
		
		//for loop to loop to input input
		for(int i = 0;i < 3;i++) {
			isValid = false;
			System.out.println("What is the name of employee " + (i+1) + "?");
			employeeName = scnr.nextLine();
			System.out.println("What is " + employeeName + "'s ID?");
			employeeID = scnr.nextLine();
			System.out.println("What is " + employeeName + "'s email address?");
			employeeEmail = scnr.nextLine();
			//do-while loop until rating it entered right
			do{
				//exception for data validation
				try{
					System.out.println("What is " + employeeName + "'s job rating? (1-10)");
					employeeRating = scnr.nextInt();
					//out of bounds
					if(employeeRating <= 0 || employeeRating > 10) {
						isValid = false;
						throw new Exception("Exception, out of range");
					}
					//is valid and in range
					else {
						isValid = true;
					}
					
				}
				//exception for wrong data type
				catch (InputMismatchException e) {
			        System.out.println("Invalid input. Please ensure that a valid integer between 1-10 are entered for the job rating!");
			        scnr.nextLine(); //eats the invalid input
			        isValid = false;
				}
				
				//exception for out of bounds
				catch (Exception e) {
					System.out.println(e.getMessage() + ". Please make sure you enter the rating on a scale of 1 - 10!");
					scnr.nextLine(); //eats the invalid input
				}
				
				
				
			}while(!isValid); // make sure it is valid before exiting
			
			//put values in the array of objects
			Employee[i] = new EmployeeInfo(employeeName, employeeEmail, employeeID, employeeRating);
			
			// print data to file after each employee entry
			Employee[i].printToFile();
		}
		
		
		
		
		
	}
}
