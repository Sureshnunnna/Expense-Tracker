# Expense-Tracker
Overview
The Expense Tracker application is a simple command-line tool that allows users to track their expenses. Users can add new expenses and view all recorded expenses. The expenses are stored in a CSV file named expenses.csv.

Features
Add Expense: Allows users to add a new expense with the date, category, amount, and a brief description.
View Expenses: Displays all recorded expenses in a tabular format.
Exit: Exits the application.
Requirements
Python 3.x
File Structure
expense_tracker.py: The main script file containing the application code.
expenses.csv: The CSV file where expenses are stored.
Usage
Running the Application
To run the Expense Tracker application, navigate to the directory containing expense_tracker.py and execute the script:

bash
Copy code
python expense_tracker.py
Menu Options
Upon running the script, you will be presented with the following menu:

markdown
Copy code
Expense Tracker Menu:
1. Add Expense
2. View Expenses
3. Exit
Adding an Expense
To add a new expense:

Select option 1 from the menu.
Enter the date of the expense in YYYY-MM-DD format.
Enter the category of the expense (e.g., Food, Travel, Utilities).
Enter the amount of the expense.
Enter a brief description of the expense.
Viewing Expenses
To view all recorded expenses, select option 2 from the menu. The expenses will be displayed in a tabular format with the following columns:

Date
Category
Amount
Description
Exiting the Application
To exit the application, select option 3 from the menu. The application will print a goodbye message and terminate.

Code Explanation
add_expense Function
The add_expense function adds a new expense to the expenses.csv file. It takes the following parameters:

date: The date of the expense.
category: The category of the expense.
amount: The amount of the expense.
description: A brief description of the expense.
The function writes the expense data to the CSV file. If the file is empty, it also writes the header row.

view_expenses Function
The view_expenses function reads and displays all expenses from the expenses.csv file. It prints the expenses in a tabular format. If the file is empty or does not exist, it prints a message indicating that no expenses are recorded.

main Function
The main function is the entry point of the application. It displays the menu and handles user input for selecting options. Based on the user's choice, it calls the appropriate function to add an expense, view expenses, or exit the application.

Exception Handling
The view_expenses function includes exception handling to catch FileNotFoundError and print an appropriate message if the expenses.csv file does not exist.

Notes
Ensure that the script has write permissions to create and modify the expenses.csv file in the directory where it is run.
The CSV file will be created in the same directory as the script if it does not already exist.



import csv
import os
from datetime import datetime

# Function to validate date format
def validate_date(date_string):
    try:
        datetime.strptime(date_string, '%Y-%m-%d')
        return True
    except ValueError:
        return False

# Function to validate amount input
def validate_amount(amount_string):
    try:
        amount = float(amount_string)
        return amount >= 0  # Ensure amount is non-negative
    except ValueError:
        return False

# Function to add an expense to the tracker
def add_expense(date, category, amount, description):
    with open('expenses.csv', 'a', newline='') as csvfile:
        fieldnames = ['Date', 'Category', 'Amount', 'Description']
        writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

        # Check if the file is empty and write headers if needed
        if os.stat('expenses.csv').st_size == 0:
            writer.writeheader()

        # Write the new expense entry
        writer.writerow({'Date': date, 'Category': category, 'Amount': amount, 'Description': description})
        print("\nExpense added successfully!\n")

# Function to view all expenses
def view_expenses():
    try:
        with open('expenses.csv', 'r') as csvfile:
            reader = csv.DictReader(csvfile)

            # Check if the file is empty
            if os.stat('expenses.csv').st_size == 0:
                print("\nNo expenses recorded yet.\n")
                return

            # Print the header
            print("\nExpense Tracker:")
            print("{:<15} {:<15} {:<10} {:<20}".format('Date', 'Category', 'Amount', 'Description'))
            print("-" * 60)

            # Print each expense entry
            for row in reader:
                print("{:<15} {:<15} ${:<9} {:<20}".format(row['Date'], row['Category'], row['Amount'], row['Description']))
            
            print()
    except FileNotFoundError:
        print("\nNo expenses recorded yet.\n")

# Main function
def main():
    while True:
        print("Expense Tracker Menu:")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Exit")

        choice = input("Enter your choice (1/2/3): ")

        if choice == '1':
            date = input("Enter the date (YYYY-MM-DD): ")
            if not validate_date(date):
                print("Invalid date format. Please use YYYY-MM-DD.")
                continue

            category = input("Enter the category: ")
            amount = input("Enter the amount: ")
            if not validate_amount(amount):
                print("Invalid amount. Please enter a non-negative number.")
                continue

            description = input("Enter a description: ")
            add_expense(date, category, float(amount), description)

        elif choice == '2':
            view_expenses()

        elif choice == '3':
            print("Exiting Expense Tracker. Goodbye!")
            break

        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()

    

![image](https://github.com/user-attachments/assets/af013941-20a3-44bc-92b4-81081b6e8255)
![image](https://github.com/user-attachments/assets/06e613b4-a4ae-4c05-8793-64dc97fee940)



