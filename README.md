# MiniBank – Java Banking Management System

## 1. Project Overview

MiniBank is a simple console-based banking management system developed using Java. It allows users to manage bank accounts and perform basic banking operations through a menu-driven interface.

The project demonstrates important Java concepts such as Object-Oriented Programming (OOP), inheritance, interfaces, exception handling, collections, file handling, serialization, and multithreading.

## 2. Features

- **Open Account:** Create a new savings account with an account number, holder name, and opening balance.
- **Deposit Money:** Add money to an existing account.
- **Withdraw Money:** Withdraw money while maintaining a minimum balance of ₹500.
- **Transfer Money:** Transfer money between two different accounts.
- **Transaction Statement:** View transaction records from the current session.
- **List Accounts:** Display all existing accounts and their balances.
- **Bank Report:** View the total number of accounts, total bank balance, and number of recorded transactions.
- **Batch Deposits:** Process multiple deposits using multiple threads.
- **Data Persistence:** Save account data to a file and load it when the program starts.
- **Input Validation:** Check for invalid amounts, duplicate account numbers, and accounts that do not exist.

## 3. Technologies Used

- **Programming Language:** Java
- **Collections:** ArrayList, List, Map, ConcurrentHashMap
- **File Handling:** FileInputStream, FileOutputStream
- **Serialization:** ObjectInputStream, ObjectOutputStream
- **Multithreading:** ExecutorService, Future, Runnable
- **Exception Handling:** IllegalArgumentException, RuntimeException
- **Development Environment:** Visual Studio Code or any Java-supported IDE

## 4. Project File Structure

The project contains the following Java files:

```text
MiniBank/
│
├── Main.java
├── Account.java
├── SavingsAccount.java
├── Repository.java
├── AccountStore.java
├── Validator.java
├── BankService.java
├── TransactionProcessor.java
└── README.md
```

The `accounts.dat` file is created or updated when account data is saved. It stores serialized account information.

## 5. Description of Java Files

### Main.java
Contains the main method and menu-driven interface. It accepts user input, calls banking operations, and handles saving and loading account data.

### Account.java
Defines the basic account details, including account number, account holder name, and balance. It also provides deposit, withdrawal, and balance-access methods.

### SavingsAccount.java
Extends the `Account` class and defines the minimum balance value of ₹500.

### Repository.java
Defines a generic interface for adding, finding, and retrieving stored accounts.

### AccountStore.java
Implements the `Repository` interface and stores account objects in a `ConcurrentHashMap`.

### Validator.java
Validates transaction amounts and checks whether an account exists.

### BankService.java
Contains the main banking operations, including account creation, deposits, withdrawals, transfers, transaction statements, account listing, and bank reports.

### TransactionProcessor.java
Uses a fixed thread pool of four worker threads to process batch deposit tasks.

## 6. Banking Rules

1. The opening balance and transaction amounts must be greater than zero.
2. Each account number must be unique.
3. The account must exist before performing a deposit, withdrawal, or transfer.
4. A withdrawal must leave at least ₹500 in the account.
5. A transfer cannot be made between the same account.
6. A transfer must leave at least ₹500 in the sender's account.
7. The batch deposit count must be between 1 and 10,000.

**Note:** The current code does not require the opening balance to be at least ₹500. The minimum-balance restriction is enforced for withdrawals and transfers.

## 7. How to Run the Project

### Requirements

- Java Development Kit (JDK) installed.
- A terminal, Command Prompt, or Visual Studio Code.
- All eight Java source files saved in the same folder.

### Step 1: Open the project folder

Open the folder containing all the Java files in Visual Studio Code or a terminal.

### Step 2: Compile the Java files

Run the following command:

```bash
javac *.java
```

### Step 3: Run the program

Execute the following command:

```bash
java Main
```

The MiniBank menu will appear in the terminal.

## 8. Menu Options

When the program starts, the following menu is displayed:

```text
--- MiniBank ---
1. Open account
2. Deposit
3. Withdraw
4. Transfer
5. Statement
6. List accounts
7. Bank report
8. Batch deposits
9. Exit
```

Enter the number corresponding to the operation you want to perform and follow the prompts.

### Example

To create an account:

1. Select option `1`.
2. Enter an account number.
3. Enter the account holder's name.
4. Enter a positive opening balance.

The program will create the account if the account number is not already in use.

## 9. Data Storage

MiniBank uses Java serialization to save account information in a file named `accounts.dat`.

- When the application starts, it attempts to load previously saved account data.
- When the user selects option `9`, the program attempts to save account data.
- If the data file does not exist, the program starts with an empty account store.

**Important:** Transaction statement entries are stored in memory and are not saved between program sessions.

## 10. Multithreading

The batch deposit feature uses an `ExecutorService` with four worker threads. Each deposit is submitted as a separate task, and the program waits for submitted tasks to complete.

This feature demonstrates basic concurrent transaction processing in Java.

## 11. Limitations

- The project is a console-based educational application.
- It does not include user authentication or PIN verification.
- Account data is stored locally rather than in a database.
- Transaction statements are not permanently stored.
- The transaction statement list is not thread-safe during concurrent batch deposits.
- The program uses `double` for monetary calculations, which may cause precision issues.
- It is not designed for real-world banking operations.

## 12. Future Improvements

- Add user login and PIN authentication.
- Use a database such as MySQL for persistent storage.
- Store transaction history permanently.
- Improve concurrency safety for transaction logging.
- Use `BigDecimal` for monetary calculations.
- Add a graphical user interface.
- Add account search, update, and deletion features.
- Generate downloadable account statements.

## 13. Learning Outcomes

Through this project, the following Java concepts can be practised:

- Classes and objects
- Encapsulation and inheritance
- Interfaces and generics
- Collections Framework
- Exception handling
- File handling and serialization
- Multithreading and concurrency
- Modular program design

## 14. Conclusion

MiniBank is a Java-based banking management project that demonstrates basic banking operations and several important programming concepts. Its modular structure separates account management, validation, data storage, banking services, and concurrent transaction processing into different classes.

The project provides a foundation for understanding how a simple banking application can be designed and implemented using Java.

---

**Project Name:** MiniBank  
**Language:** Java  
**Application Type:** Console-Based Banking Management System  
**Data File:** `accounts.dat`
