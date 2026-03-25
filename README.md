# Building-bank-account-using-python
# Bank Account App

This notebook contains a **Python OOP program** that simulates a simple bank account.  

### Features
- Deposit money
- Withdraw money (only if balance is sufficient)
- Check current balance via console input

```
class BankAccount:
    def __init__(self, account_number, account_holder):
        self.account_number = account_number
        self.account_holder = account_holder
        self.balance = 0.0
        self.pin = "1234"
        self.password = "password"

    def deposit(self, amount):
        if amount <= 0:
            print("Deposit amount must be greater than 0")
        elif amount > 1_000_000:
            print("Deposit amount exceeds the limit")
        elif amount > 100_000:
            print("Deposit inside the bank")
        else:
            self.balance += amount
            print("Deposit successful")

    def withdraw(self, amount):
        if amount <= 0:
            print("Withdrawal amount must be greater than 0")
        elif amount > self.balance:
            print("Insufficient balance")
        else:
            self.balance -= amount
            print("Withdrawal successful")

    def check_balance(self, entered_pin):
        if entered_pin == self.pin:
            print(f"Your balance is: {self.balance}")
        else:
            print("Invalid PIN")

    def update_account(self, change_password=False, new_password=None, change_pin=False, new_pin=None):
        if change_password and new_password:
            self.password = new_password
            print("Password changed successfully")
        if change_pin and new_pin:
            self.pin = new_pin
            print("PIN changed successfully")


# --- Usage ---
# Create account
account_number = int(input("Enter account number: "))
account_holder = input("Enter account holder name: ")
account = BankAccount(account_number, account_holder)

# Deposit
amount = float(input("Enter deposit amount: "))
account.deposit(amount)

# Withdraw
amount = float(input("Enter withdrawal amount: "))
account.withdraw(amount)

# Check balance
pin = input("Enter your PIN: ")
account.check_balance(pin)

# Update account
change_password = input("Do you want to change your password? (yes/no): ")
new_password = None
if change_password.lower() == "yes":
    new_password = input("Enter new password: ")

change_pin = input("Do you want to change your PIN? (yes/no): ")
new_pin = None
if change_pin.lower() == "yes":
    new_pin = input("Enter new PIN: ")

account.update_account(change_password=(change_password=="yes"), new_password=new_password,
                       change_pin=(change_pin=="yes"), new_pin=new_pin)

bank_account = BankAccount(123456, "John Doe")
bank_account.deposit(500)
bank_account.withdraw(200)
bank_account.check_balance("1234")
bank_account.update_account(change_password=True, new_password="newpass123", change_pin=True,
                          new_pin="4321")


# Print final details
print("\n--- Account Details ---")
print("Account number:", account.account_number)
print("Account holder:", account.account_holder)
print("Balance:", account.balance)

print("Account number: ", bank_account.account_number)
print("Account holder: ", bank_account.account_holder)
print("Deposit amount: ", bank_account.deposit)
print("Withdrawal amount: ", bank_account.withdraw)
print("Check balance: ", bank_account.check_balance)
print("Update account: ", bank_account.update_account)
```
# Output
`
