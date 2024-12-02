1. Class Connecte:
   Objective: 
     This class is responsible for managing the connection to the database.
   Main Method: getConnexion().
   It establishes a connection to the MySQL database (gestion_finance) using connection details (URL, username, password).
   If the connection is successful, it returns a Connection object that allows interaction with the database.

2. Class categorie:
   Objective:
     This class manages transaction categories, allowing them to be displayed and new ones added.
Methods:
   afficheCategorie(int idCategorie) : Displays the name of a transaction category given its ID (idCategorie). If the category is not found, an error message is returned.
   ajoutCategorie(String nomCategorie, String categorieType, int idCategorie) : Adds a new transaction category to the database, with a name, type, and ID. If the addition fails, an error message is returned.

3. Class Compte:
   Objective:
     This class manages user bank accounts, including displaying the balance, retrieving account information, and making deposits and withdrawals.
Methods:
   afficherSolde() : Retrieves and displays the current balance of the account, identified by idCompte.
   infosCompte() : Retrieves and displays detailed information about an account (name, type, creation date, etc.).
   deposer(double montant) : Allows depositing an amount into an account, provided the amount is positive.
   retirer(double montant) : Allows withdrawing an amount from an account, provided there are sufficient funds. If funds are insufficient, an error message is returned.

4. Class Login:
   Objective: 
     Manages user authentication and adding new accounts.
   Methods:
     identifiant(int id, String nom) : Verifies if an account exists with the given account ID (id) and name (nom). If an account is found, its ID is returned; otherwise, an error message is returned.
     ajoutPers(String nom, String type, double solde) : Adds a new account to the database with a name, account type (e.g., "Savings", "Current"), an initial balance, and the creation date.

5. Class Transaction:
   Objective: 
     Manages financial transactions between an account and a category. This includes creating new transactions, updating account balances, and retrieving transaction history.
   Methods:
     transaction(double montant, String description, int idCategorie, int idCompte) : Executes a transaction, first checking that the account balance is sufficient. If the transaction is successful, it updates the account balance and inserts a new row in the transaction table.
     historiqueTransaction(int idCompte) : Retrieves and displays the transaction history for a given account, including information such as transaction ID, category, description, amount, and date.


SUMMARY OF KEY FEATURES:
   Account Management:Account creation, displaying account information, balance, deposits, and withdrawals.
   Transaction Category Management Displaying and adding categories to organize expenses or income.
   Financial Transactions: Executing transactions (with balance verification), recording transaction history, and updating balances.
   User Authentication: User identification via an account name and ID, and adding new accounts to the database.
Database:
   The database used appears to be a MySQL database (gestion_finance), with tables such as:
      compte : Contains information about bank accounts.
      categorie : Contains categories for transactions.
      transaction : Contains transaction history, with links to accounts and categories.
   Technical Points:
      Transactions and Error Management: The Transaction class uses SQL transactions (connection.setAutoCommit(false)) to ensure operation integrity (e.g., a transaction must be fully successful or rolled back in case of failure).
   SQL Query Security: Use of PreparedStatement to prevent SQL injection and improve security.

This financial management system allows for account tracking, financial operations, category management for transactions, and ensures proper error handling and database connection management.