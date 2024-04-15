/*
* Author: Eli Ledford, Murtazza and Venessa
* Date: 04/15/2024
* Purpose: Dirived from EmployeInfo.java and has the ability to send the information to an object filewriter to be able to write to a file
*/


// SortedEmployeeInfo derived class
class SortedEmployeeInfo extends EmployeeInfo {
	private FileWriter fileWriter;
	
    //constructor to input 
	public SortedEmployeeInfo(String name, String email, int id, int rating) {
        //initializes variables by calling the constructor of the base class
		super(name, email, id, rating);
    }
    
	//method send to an aggragation object to print sorted employees to a file
	public void printSortedEmployeesToFile() {
        String content = getId() + ", " + getName() + ", Email: " + getEmail() + ", Rating: " + getRating();
        fileWriter.writeToFile(content);
    }
}
