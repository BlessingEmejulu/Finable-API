# Finable API

A Node.js/TypeScript REST API for managing virtual bank accounts and cards, with encryption for sensitive data and MongoDB integration.

## Features
- Account creation and management
- Virtual card generation
- Ledger listing with encrypted and decrypted data
- AES-256 encryption for sensitive fields
- Centralized error handling

## Getting Started

### Prerequisites
- Node.js (v16+ recommended)
- npm
- MongoDB (local or Atlas)

### Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/BlessingEmejulu/Finable-API.git
   cd Finable-API
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Create a `.env` file in the root directory:
   ```env
   MONGODB_URI=your_mongodb_connection_string
   SECRET_KEY=your-32-byte-secret-key
   ENCRYPTION_IV=your-16-byte-iv
   PORT=5000
   ```
   - `SECRET_KEY` must be 32 characters
   - `ENCRYPTION_IV` must be 16 characters

4. Start MongoDB (if running locally):
   ```sh
   mongod
   ```

5. Start the server:
   ```sh
   npm run dev
   ```

## API Endpoints

### 1. Generate Card
- **GET** `/api/card/generate-card`
- **Description:** Generates a new virtual card.
- **Response Example:**
  ```json
  {
    "cardNumber": "1234567812345678",
    "cvv": "123",
    "expiryDate": "05/28"
  }
  ```

### 2. Create Account
- **POST** `/api/accounts/accounts`
- **Body Example:**
  ```json
  {
    "firstName": "Jane",
    "surname": "Doe",
    "email": "jane.doe@example.com",
    "phoneNumber": "1234567890",
    "dateOfBirth": "1990-01-01",
    "address": "123 Main St"
  }
  ```

### 3. List All Accounts
- **GET** `/api/ledger/accounts`
- **Description:** Returns all accounts with encrypted and decrypted data.

### 4. Decrypt Data
- **POST** `/api/ledger/decrypt`
- **Body Example:**
  ```json
  {
    "encryptedData": "ENCRYPTED_STRING_HERE"
  }
  ```
- **Response Example:**
  ```json
  {
    "decryptedData": "DECRYPTED_VALUE"
  }
  ```

## Testing with Postman
- Use the [Postman Desktop Agent](https://www.postman.com/downloads/) for localhost requests.
- Import the endpoints above and test with the provided examples.

## Project Structure
- `src/models/` – Mongoose schemas
- `src/controllers/` – Route handlers
- `src/services/` – Business logic (encryption, ledger, etc.)
- `src/routes/` – Express route definitions
- `src/Utils/` – Utility functions (crypto, generator)
- `src/configs/` – Configuration and DB connection

## License
ISC
