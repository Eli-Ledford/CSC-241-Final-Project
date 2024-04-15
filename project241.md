import java.io.*;
import java.util.Scanner;

/*
* Author: Eli Ledford, Murtazza and Venessa
* Date: 04/15/2024
* Purpose: To read in a file of employees and then sort it a chose which rated employees you would like to see 
*/

public class project241 {
	
	/**\
	 * Author: Eli, Murtazza, Venessa
	 * Purpose: Recursive merge sort
	 * @param arr - the array of student
	 * @param left - most left array object
	 * @param right - most right array object
	 */
	public static void mergeSort(SortedEmployeeInfo[] arr, int left, int right) {
        if (left < right) {
            // Find the middle point
            int mid = (left + right) / 2;

            // Sort first and second halves recursively
            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);

            // Merge the sorted halves
            merge(arr, left, mid, right);
        }
    }

    /**
     * Author: Eli, Murtazza, Venessa
     * Purpose: Merge two subarrays of arr[]
     * @param arr - array used in sorting
     * @param left - most left array of the objects
     * @param mid - middle object of the array
     * @param right - msot right object of the array
     */
    public static void merge(SortedEmployeeInfo[] arr, int left, int mid, int right) {
        // Sizes of two subarrays to be merged
        int n1 = mid - left + 1;
        int n2 = right - mid;

        // Create temporary arrays
        SortedEmployeeInfo[] L = new SortedEmployeeInfo[n1];
        SortedEmployeeInfo[] R = new SortedEmployeeInfo[n2];

        // Copy data to temporary arrays L[] and R[]
        for (int i = 0; i < n1; i++) {
            L[i] = arr[left + i];
        }
        for (int j = 0; j < n2; j++) {
            R[j] = arr[mid + 1 + j];
        }

        // Merge the temporary arrays
        int i = 0, j = 0;
        int k = left; // Initial index of merged subarray
        while (i < n1 && j < n2) {
            if (L[i].getRating() <= R[j].getRating()) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements of L[] and R[] if any
        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }
        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }
	
    //main starting point of the program
    public static void main(String[] args) {
        // Declare scanner object for file input
        Scanner fileScanner = null;
        //make sure the file is found and read in correctly
        try {
            fileScanner = new Scanner(new File("Employees.txt"));
        } 
        catch (FileNotFoundException e) {
            System.out.println("File not found: Employees.txt");
        }

        // Declare array of EmployeeInfo objects
        SortedEmployeeInfo[] employees = new SortedEmployeeInfo[100];

        // Declare variables
        String employeeEmail;
        int employeeID;
        String employeeName;
        int employeeRating;

        // Loop to read input from the file
        for (int i = 0; i < 100; i++) {
            // Read employee details from the file
            employeeName = fileScanner.nextLine();
            employeeID = fileScanner.nextInt();
            fileScanner.nextLine(); // Consume the newline character after reading the int
            employeeEmail = fileScanner.nextLine();
            employeeRating = fileScanner.nextInt();
            fileScanner.nextLine(); // Consume the newline character after reading the int

            // Store values in the array of objects
            employees[i] = new SortedEmployeeInfo(employeeName, employeeEmail, employeeID, employeeRating);

            
        }
        
        // Sort employees based on ratings using recursive merge sort
        mergeSort(employees, 0, employees.length - 1);
        
        
        //prints the sorted employee array into the file
        for (SortedEmployeeInfo employee : employees) {
        	//calls the corresponding employee to print
        	employee.printSortedEmployeesToFile();// Print sorted employees
        }

        // Close the file scanner
        fileScanner.close();
    }
}
