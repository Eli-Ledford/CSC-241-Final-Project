//Used for writing to a file
import java.io.FileWriter;
import java.io.PrintWriter;
import java.io.IOException;

public class EmployeeInfo {
	//declare variables and give them default values
	private int rating = -1;
	private String name = "NoName";
	private String email = "NoName";
	private String id = "noID";

	// Another constructor to initialize variables with value and take away default value
	public EmployeeInfo(String name, String email, String id, int rating) {
		this.name = name;
		this.id = id;
		this.rating = rating;
		this.email = email;
	}

	// Prints name and rating on one line
	public void printToFile() {
		// Define the file name
        String fileName = "EmployeeInformation.txt";

        try {
            // Create a FileWriter object to write to the file
            FileWriter fileWriter = new FileWriter(fileName, true);
            
            // Create a PrintWriter object to write formatted text to the FileWriter
            PrintWriter printWriter = new PrintWriter(fileWriter);

            // Write to the file with Employee information
            printWriter.println("Name of employee: " + name);
            printWriter.println(name + "'s ID: " + id);
            printWriter.println(name + "'s email: " + email);
            printWriter.println(name + "'s rating: " + rating);printWriter.println("Hello, world!");
            printWriter.println();            
            
            // Close the PrintWriter and FileWriter
            printWriter.close();
            fileWriter.close();

            System.out.println("Data has been written to the file.");
        } catch (IOException e) {
            // Handle any exceptions that occur during file operations
            System.out.println("An error occurred while writing to the file: " + e.getMessage());
            e.printStackTrace();
        }
		
	}

}
