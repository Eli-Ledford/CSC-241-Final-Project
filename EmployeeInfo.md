//Used for writing to a file

/*
* Author: Eli Ledford, Murtazza and Venessa
* Date: 04/15/2024
* Purpose: Has the information of the employees and is a base class
*/

public class EmployeeInfo {
	//declare variables and give them default values
	private int rating = -1;
	private String name = "NoName";
	private String email = "NoName";
	private int id = -1;

	// Another constructor to initialize variables with value and take away default value
	public EmployeeInfo(String name, String email, int id, int rating) {
		this.name = name;
		this.id = id;
		this.rating = rating;
		this.email = email;
	}
	
	//method returns the name of employee
	public String getName() {
		return name;
	}
	
	//method returns id of employee
	public int getId() {
		return id;
	}
	
	//method returns the rating of the employee
	public int getRating() {
		return rating;
	}
	
	//method returns the email of employee
	public String getEmail() {
		return email;
	}

}
