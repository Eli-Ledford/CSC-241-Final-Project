import java.io.*;

/*
* Author: Eli Ledford, Murtazza and Venessa
* Date: 04/15/2024
* Purpose: Has the ability to open a file and write to the file with the information given by the SortedEmployees.java class
*/

public class FileWriter {
	//file name variable
    private String fileName = "SortedEmployees.txt";
    
    // default constructor
    public FileWriter() {
    	fileName = "SortedEmployees.txt";
    }

    //constructor to initialize
    public FileWriter(String fileName) {
        this.fileName = fileName;
    }
    
    // Method to get the file name
    public String getFileName() { 
        return fileName;
    }
    
    // Method to set the file name
    public void setFileName(String file) {
        fileName = file;
    }
    
    // Method to write content to the file
    public void writeToFile(String content) {
        //make sure that the file opens and is found
    	try (PrintWriter printWriter = new PrintWriter(new BufferedWriter(new java.io.FileWriter(fileName, true)))) {
            // Write content to the file
            printWriter.println(content);
        } 
        //catch all exceptions
        catch (IOException e) {
            // Handle any IO exception that may occur
            System.out.println("An error occurred while writing to the file: " + e.getMessage());
        }
    }
}
