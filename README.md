import java.util.Scanner;
class CreditCard {
    String cardNumber;
    String customerName;
    double creditLimit;
    double availableLimit;
    double totalSpent;
    public CreditCard(String cardNumber, String customerName, double creditLimit) {
        this.cardNumber = cardNumber;
        this.customerName = customerName;
        this.creditLimit = creditLimit;
        this.availableLimit = creditLimit;
        this.totalSpent = 0;
    }
    public void viewCardDetails() {
        System.out.println("\n----------- CARD DETAILS -----------");
        System.out.println("Customer Name : " + customerName);
        System.out.println("Card Number   : " + cardNumber);
        System.out.println("Credit Limit  : ₹" + creditLimit);
        System.out.println("Available Limit : ₹" + availableLimit);
        System.out.println("------------------------------------");
    }
    public void makePurchase(double amount) {
        if (amount <= availableLimit) {
            availableLimit -= amount;
            totalSpent += amount;
            System.out.println("\nPurchase Successful!");
            System.out.println("Available Limit : ₹" + availableLimit);
        } else {
            System.out.println("\nInsufficient Credit Limit!");
        }
    }
    public void generateBill() {
        System.out.println("\n----------- BILL DETAILS -----------");
        System.out.println("Card Number : " + cardNumber);
        System.out.println("Credit Limit : ₹" + creditLimit);
        System.out.println("Total Spent : ₹" + totalSpent);
        System.out.println("Outstanding Amount : ₹" + totalSpent);
        System.out.println("------------------------------------");
    }
    public void payBill(double amount) {
        if (amount > totalSpent) {                                          
            amount = totalSpent;
        }
        totalSpent -= amount;
        availableLimit += amount;
        System.out.println("\nPayment Successful!");
        System.out.println("Remaining Outstanding : ₹" + totalSpent);
    }
    public void checkAvailableLimit() {
        System.out.println("\nAvailable Credit Limit : ₹" + availableLimit);
    }
    public void calculateInterest() {
        double interest = totalSpent * 0.03;
        System.out.println("\nOutstanding Amount : ₹" + totalSpent);
        System.out.println("Interest (3%) : ₹" + interest);
    }
}
public class creditcard {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        CreditCard card = null;
        while (true) {
            System.out.println("==========Credit Card Processing System==========");
            System.out.println("1. Apply Credit Card");
            System.out.println("2. View Card Details");
            System.out.println("3. Make Purchase");
            System.out.println("4. Generate Bill");
            System.out.println("5. Pay Bill");
            System.out.println("6. Check Available Limit");
            System.out.println("7. Calculate Interest");
            System.out.println("8. Exit");
            System.out.print("\nEnter your choice: ");
            int choice = sc.nextInt();
            switch (choice) {
                case 1:
                    sc.nextLine();
                    System.out.print("Enter Customer Name : ");
                    String name = sc.nextLine();
                    System.out.print("Enter Age : ");
                    int age = sc.nextInt();
                    System.out.print("Enter Annual Income : ");
                    double income = sc.nextDouble();
                    if (age >= 18 && income >= 300000) {
                        card = new CreditCard(
                                "CC101",
                                name,
                                100000);
                        System.out.println("\nCredit Card Issued Successfully!");
                        System.out.println("Card Number : CC101");
                        System.out.println("Credit Limit : ₹100000");
                    } else {
                        System.out.println("\nApplication Rejected!");
                    }
                    break;
                case 2:
                    if (card != null)
                        card.viewCardDetails();
                    else
                        System.out.println("\nApply for a card first!");
                    break;
                case 3:
                    if (card != null) {
                        System.out.print("Enter Purchase Amount : ");
                        double purchase = sc.nextDouble();
                        card.makePurchase(purchase);
                    } else {
                        System.out.println("\nApply for a card first!");
                    }
                    break;
                case 4:
                    if (card != null)
                        card.generateBill();
                    else
                        System.out.println("\nApply for a card first!");
                    break;
                case 5:
                    if (card != null) {
                        System.out.print("Enter Payment Amount : ");
                        double payment = sc.nextDouble();
                        card.payBill(payment);
                    } else {
                        System.out.println("\nApply for a card first!");
                    }
                    break;
                case 6:
                    if (card != null)
                        card.checkAvailableLimit();
                    else
                        System.out.println("\nApply for a card first!");
                    break;
                case 7:
                    if (card != null)
                        card.calculateInterest();
                    else
                        System.out.println("\nApply for a card first!");
                    break;
                case 8:
                    System.out.println("\nThank You For Using");
                    System.out.println("Credit Card Management System!");
                    sc.close();
                    System.exit(0);
                default:
                    System.out.println("\nInvalid Choice!");
            }
        }
    }
}
