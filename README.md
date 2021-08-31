# My first project

## Introduction

After many searches for project ideas I said to try this one, namely Banking Application. It's my first project, it's not very complicated, but I'm proud of the work I've done. I thought that nowadays a lot of people use banking applications and that it would be interesting if I created one, even if at a basic level.


## Code Samples

import java.util.Scanner;

public class BankingApplication {

    public static void main(String[] args) {

        BankAccount obj = new BankAccount("ABC","XY0000");
        obj.showMenu();
    }
}

class BankAccount {

    int balance;
    int previousTransaction;
    String customerName;
    String customerId;

    BankAccount(String cName, String cId) {

        customerName = cName;
        customerId = cId;

    }


    void deposit (int amount) {

        if (amount != 0) {
            balance = balance + amount;
            previousTransaction = amount;
        }
    }

    void withdraw (int amount) {

        if (amount != 0){
            balance = balance - amount;
            previousTransaction = - amount;
        }
    }

    void getPreviousTransaction(){

    if (previousTransaction > 0){
        System.out.println("Deposited: " + previousTransaction);
    }
    else if (previousTransaction < 0){
        System.out.println("Withdrawn: "+Math.abs(previousTransaction));
    }
    else {
        System.out.println("No transaction occured.");
    }
    }

    void showMenu () {

        char option = '\0';
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome, " + customerName);
        System.out.println("Your ID is: " + customerId);
        System.out.println("\n");
        System.out.println("A. Check balance");
        System.out.println("B. Deposit");
        System.out.println("C. Withdraw");
        System.out.println("D. Previous transaction");
        System.out.println("E. Exit");

        do {
            System.out.println("**********");
            System.out.println("Enter an option ");
            System.out.println("**********");
            option = scanner.next().charAt(0);
            System.out.println("\n");

            switch (option) {

                case 'A':
                    System.out.println("----------");
                    System.out.println("Balance = "+ balance + " RON ");
                    System.out.println("----------");
                    System.out.println("\n");
                    break;

                case 'B':
                    System.out.println("----------");
                    System.out.println("Enter an amount to deposit: ");
                    System.out.println("----------");
                    int amount = scanner.nextInt();
                    deposit(amount);
                    System.out.println("\n");
                    break;

                case 'C':
                    System.out.println("----------");
                    System.out.println("Enter an amount to withdraw: ");
                    System.out.println("----------");
                    int amount2 = scanner.nextInt();
                    withdraw(amount2);
                    System.out.println("\n");
                    break;

                case 'D':
                    System.out.println("----------");
                    getPreviousTransaction();
                    System.out.println("----------");
                    System.out.println("\n");
                    break;

                case 'E':
                    System.out.println("----------");
                    break;

                default:
                    System.out.println("Invalid choice! Please enter your option again!");
                    break;

            }
        } while (option != 'E');
        System.out.println("Thank you for using our services!");
        }
    }



