import java.util.Scanner;

public class InterestCalculator {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        // Enter number of months
        System.out.print("Enter number of months: ");
        int months = input.nextInt();

        // Specify that program is not expected to handle more than 5 months
        if (months <= 5) {
            
            // Enter investment amount
            System.out.print("Enter amount: ");
            int investmentAmount = input.nextInt();

            // Enter compound interest rate in % (per annum)
            System.out.print("Enter interest rate (%): ");
            int rate = input.nextInt();

            // Cast inputted interest rate as double variable
            double interestRate = rate * 0.01 / 12;

            // Insert blank line and display table headings
            System.out.println("");
            System.out.println("Month  Opening Balance  "
                + "Interest  Closing Balance");

            // Formulas for calculation
            // Opening balance = P(1 + r) ^ t - 1
            // Interest = P(1 + r) ^ t - P
            // Closing balance = P(1 + r) ^ t
            // Where P = investmentAmount, r = interestRate, and t = months

            for (int i = 1; i <= months; i++) {

                // Cast opening and closing balance as double variables
                double open = investmentAmount * Math.pow((1 + interestRate), 
                    i - 1);
                double close = investmentAmount * Math.pow((1 + interestRate),
                    i);
        
                // Print table rows
                // Display month column
                System.out.print(i + "      ");

                // Display opening balance column
                String openingBalance = String.format("%-17.2f", 
                    (investmentAmount * Math.pow((1 + interestRate),i - 1))); 
                System.out.print(openingBalance);

                // Display interest amount column
                double interestRateString = close - open;
                String interest = String.format("%-10.2f", interestRateString);
                System.out.print(interest);
        
                // Display closing balance column
                double closingBalanceString = (investmentAmount * 
                    Math.pow((1 + interestRate), i));
                String closingBalance = String.format("%-3.2f", 
                    closingBalanceString);
                System.out.println(closingBalance);
            }
            
        }   

        else {
            System.out.println("Program is not expected to" + 
              " handle more than 5 months");
        }

    }
}
