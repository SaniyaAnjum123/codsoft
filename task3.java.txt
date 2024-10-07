import java.util.Scanner;

// BankAccount class to represent the user's bank account
class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposit successful. New balance: " + balance);
    }

    public boolean withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
            System.out.println("Withdrawal successful. New balance: " + balance);
            return true;
        } else {
            System.out.println("Insufficient funds. Withdrawal failed.");
            return false;
        }
    }
}

// ATM class to represent the ATM machine
class ATM {
    private BankAccount bankAccount;

    public ATM(BankAccount bankAccount) {
        this.bankAccount = bankAccount;
    }

    public void displayMenu() {
        System.out.println("Welcome to the ATM.");
        System.out.println("1. Withdraw");
        System.out.println("2. Deposit");
        System.out.println("3. Check Balance");
        System.out.println("4. Exit");
    }

    public void processTransaction(int choice) {
        Scanner scanner = new Scanner(System.in);
        switch (choice) {
            case 1:
                System.out.print("Enter amount to withdraw: ");
                double withdrawAmount = scanner.nextDouble();
                if (withdrawAmount > 0) {
                    bankAccount.withdraw(withdrawAmount);
                } else {
                    System.out.println("Invalid amount.");
                }
                break;
            case 2:
                System.out.print("Enter amount to deposit: ");
                double depositAmount = scanner.nextDouble();
                if (depositAmount > 0) {
                    bankAccount.deposit(depositAmount);
                } else {
                    System.out.println("Invalid amount.");
                }
                break;
            case 3:
                System.out.println("Your balance is: " + bankAccount.getBalance());
                break;
            case 4:
                System.out.println("Thank you for using the ATM.");
                break;
            default:
                System.out.println("Invalid choice.");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount userAccount = new BankAccount(1000.0); // Initial balance of $1000
        ATM atm = new ATM(userAccount);

        Scanner scanner = new Scanner(System.in);
        int choice;
        do {
            atm.displayMenu();
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            atm.processTransaction(choice);
        } while (choice != 4);
    }
}