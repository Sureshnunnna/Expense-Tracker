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


![image](https://github.com/Sureshnunnna/Expense-Tracker/assets/107661714/6322f7fa-bff2-48eb-aa97-f18ea1c52587)


