# bankAccount
Making a bank account with java
public class BankAccount {
    private static int accountCounter = 1000; 
    private int accountNumber;               
    private String accountHolderName;        
    private double balance;                  

    
    public BankAccount(String accountHolderName, double initialDeposit) {
        this.accountNumber = ++accountCounter;   
        this.accountHolderName = accountHolderName;
        if (initialDeposit >= 0) {
            this.balance = initialDeposit;
        } else {
            System.out.println("Initial deposit cannot be negative. Setting balance to 0.");
            this.balance = 0;
        }
    }
    
    public BankAccount(String accountHolderName) {
        this(accountHolderName, 0.0);
    }

   
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Successfully deposited $" + amount);
        } else {
            System.out.println("Deposit amount must be greater than zero.");
        }
    }

    
    public void withdraw(double amount) {
        if (amount > 0) {
            if (balance >= amount) {
                balance -= amount;
                System.out.println("Successfully withdrew $" + amount);
            } else {
                System.out.println("Insufficient balance! Withdrawal failed.");
            }
        } else {
            System.out.println("Withdrawal amount must be greater than zero.");
        }
    }

  
    public double getBalance() {
        return balance;
    }

    // Method to display account information
    public void displayAccountInfo() {
        System.out.println("\nAccount Information:");
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Account Holder: " + accountHolderName);
        System.out.println("Current Balance: $" + balance);
    }

    // Main method for testing the class
    public static void main(String[] args) {
        // Create accounts
        BankAccount account1 = new BankAccount("Mr. Rahim", 500.0);
        BankAccount account2 = new BankAccount("Mr. Karim");

        // Display initial account details
        account1.displayAccountInfo();
        account2.displayAccountInfo();

        // Perform transactions
        account1.deposit(200);
        account1.withdraw(100);
        account1.displayAccountInfo();

        account2.deposit(300);
        account2.withdraw(400); // Insufficient balance
        account2.withdraw(50);
        account2.displayAccountInfo();
    }
}
