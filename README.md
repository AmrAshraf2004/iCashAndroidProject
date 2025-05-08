src.zip file contains all files related to project including layouts

📱 iCash Wallet – Project Overview and Functional Description
The iCash app is a mobile digital wallet built with Android Studio using Java, Firebase Realtime Database, and Firebase Authentication. It allows users to manage money digitally in a secure and seamless way. The app is designed to mimic features of modern e-wallets, enabling users to deposit, withdraw, send, and track money transactions, all through a clean and intuitive interface.

Once users launch the app, they are greeted with a splash screen, followed by a login or signup screen. Firebase Authentication manages account creation and login securely. Upon successful login, users are redirected to the HomeFragment, which displays a personalized greeting and their current wallet balance. A one-time notification is triggered here using WorkManager, informing the user that their session has begun.

From the home screen, users can access three main functions:

Deposit money: Adds funds to the user's digital wallet by selecting one of their linked cards.

Withdraw money: Deducts a specified amount from their wallet and logs the transaction.

Send money: Transfers a chosen amount to another user, identified by their account number.

Users can add or remove credit/debit cards through the AccountFragment. These cards are linked to their Firebase UID, preventing duplication and allowing easy lookup for deposits/withdrawals. Validation is in place to ensure proper format for card numbers, expiry dates, and CVVs.

Each financial operation (deposit, withdraw, send) is logged in Firebase under a transactions node, with clear metadata such as transaction ID, amount, type, date, sender/receiver details, and status. These logs are then retrievable and displayed to the user in a ViewTransactionsFragment, where transactions are split into "Sent" and "Received" sections for clarity.

The transaction viewer fetches all relevant transactions where the logged-in user is either a sender or recipient. It dynamically pulls additional info like the recipient’s account number using Firebase queries — ensuring accurate and complete details are always shown.

Behind the scenes, session management is handled by a SessionManager singleton. It caches the current user object for performance and consistency across fragments. However, wallet balances are always updated in Firebase to maintain accuracy and sync across devices.

The app also makes thoughtful use of LiveData (initially in the HomeViewModel) to update the UI reactively when the user's data changes — though eventually much of this was merged into the fragment itself for simplicity.

🛠 Technical Summary:
Language: Java

Architecture: Fragment-based UI with View Binding

Backend: Firebase Realtime Database + FirebaseAuth

Session Handling: Singleton SessionManager

Transactions: All monetary actions create detailed transaction logs

Card Management: Add/remove cards tied to user UID

Balance Handling: Synced updates to Firebase + UI

Notifications: One-time welcome via WorkManager

Security: Basic validations (card format, balance checks, user ID constraints)

👤 What Users Can Do:
Sign up and log in securely

View their profile and account number

Add valid credit/debit cards

Deposit and withdraw money using linked cards

Send funds to others via account number

View complete history of all sent and received transactions

Log out and clear session data
