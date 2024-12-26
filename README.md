---

# BankingAPI

A lightweight banking system API built using **ASP.NET Core 6**, **Entity Framework Core**, and **SQLite**. This application allows you to perform basic banking operations such as creating accounts, deposits, withdrawals, transfers, and balance inquiries.

---

## Prerequisites

Before running this application, ensure you have the following installed:

1. **.NET 6 SDK**  
   - [Download .NET 6 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)
2. **SQLite**  
   - SQLite is embedded in the application. Optionally, you can use [DB Browser for SQLite](https://sqlitebrowser.org/dl/) to view the database.
3. **Visual Studio**  
   - Compatible with older versions of Visual Studio that support .NET 6.

---

## Getting Started

### Clone the Repository

Clone the repository to your local machine:
```bash
git clone https://github.com/MostafaAlaa297/BankingAPI.git
cd BankingAPI
```

### Database Setup

1. **Install Entity Framework Core Tools**:
   ```bash
   dotnet tool install --global dotnet-ef
   ```

2. **Apply Migrations**:
   ```bash
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   ```

3. **Verify Database Configuration**:  
   Open `appsettings.json` and ensure the SQLite connection string is correct:
   ```json
   {
       "ConnectionStrings": {
           "DefaultConnection": "Data Source=banking.sqlite"
       }
   }
   ```

4. **Explore the Database** (Optional):  
   Use [DB Browser for SQLite](https://sqlitebrowser.org/dl/) to view the database.

---

## Running the Application

1. Open the solution (`BankingAPI.sln`) in **Visual Studio**.
2. Build the solution to restore dependencies:
   ```bash
   dotnet build
   ```
3. Run the application:
   ```bash
   dotnet run
   ```
4. Access the API using Swagger for interactive documentation:  
   - Navigate to: [http://localhost:5000/swagger](http://localhost:5000/swagger) (adjust port if needed).

---

## API Endpoints

### 1. **Create Account**
- **URL**: `/api/accounts/create`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "accountNumber": "string",
    "accountType": "string",
    "interestRate": 0,
    "overdraftLimit": 0
  }
  ```
- **Response**:
  ```json
  {
    "Message": "Account created successfully",
    "Account": {
      "accountNumber": "string",
      "accountType": "string",
      "balance": 0.0
    }
  }
  ```

### 2. **Deposit**
- **URL**: `/api/accounts/deposit`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "accountNumber": "string",
    "amount": 100.0
  }
  ```
- **Response**:
  ```json
  {
    "balance": 100.0
  }
  ```

### 3. **Withdraw**
- **URL**: `/api/accounts/withdraw`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "accountNumber": "string",
    "amount": 50.0
  }
  ```
- **Response**:
  ```json
  {
    "balance": 50.0
  }
  ```

### 4. **Transfer**
- **URL**: `/api/accounts/transfer`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "sourceAccountNumber": "string",
    "targetAccountNumber": "string",
    "amount": 50.0
  }
  ```
- **Response**:
  ```json
  {
    "message": "Transfer done successfully. Source balance: 50.0 Target balance: 150.0"
  }
  ```

### 5. **Get Balance**
- **URL**: `/api/accounts/{id}/balance`
- **Method**: `GET`
- **Response**:
  ```json
  {
    "balance": "string",
    "accountType": "string"
  }
  ```

---

## Testing the Application

This project includes unit tests for key operations such as deposits, withdrawals, and transfers.

1. Run tests using the following command:
   ```bash
   dotnet test
   ```
2. Ensure all tests pass successfully.

---

## Notes

- This project uses **.NET 6** for compatibility with older Visual Studio versions. Please ensure your development environment supports this version.
- For any issues, feel free to open an issue in the [GitHub repository](https://github.com/MostafaAlaa297/BankingAPI).

---
