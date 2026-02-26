// Angel Guerra
// CTE Software Development 2
// Instructor: Mr. Gross

import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class LetterFrequency2 {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        File file = new File("UserData.txt");

        try {

            FileWriter writer = new FileWriter(file);

            // This loops 5 times for 5 users 
            for (int i = 1; i <= 5; i++) {

                System.out.println("Enter name for User " + i + ": ");
                String name = input.nextLine();

                System.out.println("Enter address for User " + i + ": ");
                String address = input.nextLine();

                System.out.println("Enter city for User " + i + ": ");
                String city = input.nextLine();

                System.out.println("Enter state for User " + i + ": ");
                String state = input.nextLine();

                System.out.println("Enter phone number for User " + i + ": ");
                String phone = input.nextLine();

                // save data
                writer.write(name + "|" + address + "|" + city + "|" + state + "|" + phone + "\n");
            }

            writer.close();
            System.out.println("\nData successfully written to file.\n");

        } catch (IOException e) {
            System.out.println("Error writing to file.");
        }

        // This reads the file back
        try {

            Scanner fileReader = new Scanner(file);

            System.out.println("----- Reading Data From File -----");

            int userNumber = 1;

            while (fileReader.hasNextLine()) {

                String line = fileReader.nextLine();

                // Split using pipe symbol
                String[] parts = line.split("\\|");

                System.out.println("\nUser " + userNumber + " Information:");
                System.out.println("Name: " + parts[0]);
                System.out.println("Address: " + parts[1]);
                System.out.println("City: " + parts[2]);
                System.out.println("State: " + parts[3]);
                System.out.println("Phone: " + parts[4]);

                userNumber++;
            }

            fileReader.close();

        } catch (IOException e) {
            System.out.println("Error reading file.");
        }

        input.close();
    }
}
