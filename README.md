# Send-Money-App
Project Overview
This is a Flutter application for a "Send Money" system with the following features:
•	Login/logout with username/password.
•	View wallet balance with a show/hide toggle.
•	Send money with error/success feedback.
•	View transaction history.
•	Offline mode for cached data access.


How to Run Unit Tests
Unit tests are located in the test/login_test.dart file.
1.	Run Tests
flutter test
2.	View Results
o	Pass/Fail results will be displayed in the termina
Design Documentation
Class Diagram
This diagram represents the relationship between core components.
  [ApiService]   <-->  [LocalStorageService]
     |                        |
     |                        |
  [LoginScreen]    [WalletScreen] <--> [TransactionHistoryScreen]
     |                        |
     +---------> [SendMoneyScreen]

a. ApiService: Handles API requests for login, wallet balance, and transactions.
b. LocalStorageService: Manages local caching of data (wallet balance, transactions).
c.  Screens: Implement the UI and interact with models and services.


Sequence Diagram
Login Flow
User -> LoginScreen: Enter credentials
LoginScreen -> ApiService: Verify credentials
ApiService -> LoginScreen: Success/Failure response
LoginScreen -> WalletScreen: Navigate on success

User -> SendMoneyScreen: Enter amount
SendMoneyScreen -> ApiService: Post transaction
ApiService -> SendMoneyScreen: Success/Failure response
SendMoneyScreen -> LocalStorageService: Cache transaction (if online)

User -> TransactionHistoryScreen: View history
TransactionHistoryScreen -> LocalStorageService: Fetch cached transactions
LocalStorageService -> TransactionHistoryScreen: Return cached data
