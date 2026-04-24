#include <iostream>
#include <fstream>
#include <string>

using namespace std;

// Function for user registration
void registerUser() 
{
    string username, password;
    bool userExists = false;

    cout << "\n--- Registration ---\n";

    cout << "Enter username: ";
    cin >> username;

    cout << "Enter password: ";
    cin >> password;

    ifstream inFile("users.txt");
    string fileUser, filePass;

    // Check if username already exists
    while (inFile >> fileUser >> filePass) 
	{
        if (fileUser == username) 
		{
            userExists = true;
            break;
        }
    }
    inFile.close();

    if (userExists) 
	{
        cout << "Username already exists! Try another.\n";
    } 
    else 
	{
        ofstream outFile("users.txt", ios::app);
        outFile << username << " " << password << endl;
        outFile.close();

        cout << "Registration successful!\n";
    }
}

// Function for user login
void loginUser() 
{
    string username, password;
    bool loginSuccess = false;

    cout << "\n--- Login ---\n";

    cout << "Enter username: ";
    cin >> username;

    cout << "Enter password: ";
    cin >> password;

    ifstream inFile("users.txt");
    string fileUser, filePass;

    // Verify credentials
    while (inFile >> fileUser >> filePass) {
        if (fileUser == username && filePass == password) {
            loginSuccess = true;
            break;
        }
    }
    inFile.close();

    if (loginSuccess) 
	{
        cout << "Login successful! Welcome " << username << " ??\n";
    } 
    else {
        cout << "Invalid username or password.\n";
    }
}

int main() 
{
    int choice;

    cout << "1. Register\n";
    cout << "2. Login\n";
    cout << "Enter your choice: ";
    cin >> choice;

    if (choice == 1) 
	{
        registerUser();
    } 
    else if (choice == 2) 
	{
        loginUser();
    } 
    else 
	#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> accountNumbers;
    vector<string> names;
    vector<double> balances;

    int choice;

    do {
        cout << "\n--- Banking System ---\n";
        cout << "1. Create Account\n";
        cout << "2. Deposit\n";
        cout << "3. Withdraw\n";
        cout << "4. Transfer\n";
        cout << "5. Show Details\n";
        cout << "6. Exit\n";
        cout << "Enter choice: ";
        cin >> choice;

        if (choice == 1) {
            int accNo;
            string name;

            cout << "Enter name: ";
            cin >> name;

            cout << "Enter account number: ";
            cin >> accNo;

            accountNumbers.push_back(accNo);
            names.push_back(name);
            balances.push_back(0);

            cout << "Account created successfully.\n";
        } 
        else if (choice >= 2 && choice <= 5) {
            int accNo;
            cout << "Enter account number: ";
            cin >> accNo;

            int index = -1;

            // Find account
            for (int i = 0; i < accountNumbers.size(); i++) {
                if (accountNumbers[i] == accNo) {
                    index = i;
                    break;
                }
            }

            if (index == -1) {
                cout << "Account not found.\n";
            } 
            else {
                if (choice == 2) {
                    double amount;
                    cout << "Enter amount: ";
                    cin >> amount;

                    if (amount > 0) {
                        balances[index] += amount;
                        cout << "Deposit successful.\n";
                    } 
                    else {
                        cout << "Invalid amount.\n";
                    }
                } 
                else if (choice == 3) {
                    double amount;
                    cout << "Enter amount: ";
                    cin >> amount;

                    if (amount > 0 && amount <= balances[index]) {
                        balances[index] -= amount;
                        cout << "Withdrawal successful.\n";
                    } 
                    else {
                        cout << "Insufficient balance or invalid amount.\n";
                    }
                } 
                else if (choice == 4) {
                    int toAcc;
                    double amount;

                    cout << "Enter receiver account number: ";
                    cin >> toAcc;

                    cout << "Enter amount: ";
                    cin >> amount;

                    int toIndex = -1;

                    // Find receiver
                    for (int i = 0; i < accountNumbers.size(); i++) {
                        if (accountNumbers[i] == toAcc) {
                            toIndex = i;
                            break;
                        }
                    }

                    if (toIndex == -1) {
                        cout << "Receiver not found.\n";
                    } 
                    else {
                        if (amount > 0 && amount <= balances[index]) {
                            balances[index] -= amount;
                            balances[toIndex] += amount;
                            cout << "Transfer successful.\n";
                        } 
                        else {
                            cout << "Transfer failed.\n";
                        }
                    }
                } 
                else if (choice == 5) {
                    cout << "\nName: " << names[index] << endl;
                    cout << "Account Number: " << accountNumbers[index] << endl;
                    cout << "Balance: " << balances[index] << endl;
                }
            }
        } 
        else if (choice == 6) {
            cout << "Exiting...\n";
        } 
        else {
            cout << "Invalid choice.\n";
        }

    } while (choice != 6);

    return 0;
}{
        cout << "Invalid choice.\n";
    }

    return 0;
}
