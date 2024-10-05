# 👋 Welcome to My GitHub!

I'm Aashish, a passionate developer focused on mastering backend development 🚀. This repository contains the API documentation for my Express.js application.

---

## 📚 API Documentation

### Base URL
The base URL for the API is:
https://aashishinventory.up.railway.app/
### Authentication Endpoints

#### 1. **Register a User**
- **Endpoint**: `POST /auth/register`
- **Description**: Registers a new user.
- **Required Fields**:
  - `username`
  - `email`
  - `password`
  - `phoneNumber`
- **Limits**: Auth limiter allows **5 requests per 15 minutes**.

#### 2. **Login User**
- **Endpoint**: `POST /auth/login`
- **Description**: Authenticates a user.
- **Required Fields**:
  - `email`
  - `password`
- **Limits**: Auth limiter allows **5 requests per 15 minutes**.

#### 3. **Update Admin User**
- **Endpoint**: `PATCH /auth/update/:id`
- **Description**: Updates the admin user’s details.
- **Required Parameters**:
  - `id`: User ID
- **Fields to Update**:
  - `logo`
  - `company`
  - `pan`
  - `products`
- **Note**: Requires payment protection; cannot update without a subscription.

#### 4. **Logout User**
- **Endpoint**: `DELETE /api/auth/logout/:id`
- **Description**: Logs out the user.
- **Required Parameters**:
  - `id`: Admin ID

#### 5. **Reset Password**
- **Request Email**:
  - **Endpoint**: `POST /api/auth/reset-password`
  - **Description**: Sends an email for password reset.
  - **Required Field**: `currentEmail`
  
- **Change Password**:
  - **Endpoint**: `PATCH /api/auth/reset-password/:token`
  - **Description**: Changes the password using a reset token.
  - **Required Fields**: `newPassword`

### Cashier Management Endpoints

#### 1. **Create Cashier Controller**
- **Endpoint**: `POST /api/cashier/:id/cashier`
- **Description**: Creates a new cashier by the admin.
- **Required Parameters**:
  - `id`: Admin ID
- **Required Fields**:
  - `email`
  - `password`
  - `phoneNumber`
- **Note**: Admin protected middleware required.

#### 2. **Get All Cashiers**
- **Endpoint**: `GET /api/cashier/:id`
- **Description**: Retrieves all cashiers associated with the admin.
- **Required Parameters**:
  - `id`: Admin ID

#### 3. **Cashier Login**
- **Endpoint**: `POST /api/cashier/login`
- **Description**: Authenticates a cashier.
- **Required Fields**:
  - `email`
  - `password`

#### 4. **Delete Cashier**
- **Endpoint**: `DELETE /api/cashier/:id/:cashierId`
- **Description**: Deletes a cashier account.
- **Required Parameters**:
  - `id`: Admin ID
  - `cashierId`: Cashier ID
- **Note**: Admin protected middleware required.

### Sales Endpoints

#### 1. **Make Sale**
- **Endpoint**: `POST /api/sale/sale-product/:id/:productId`
- **Description**: Creates a sale for a product.
- **Required Parameters**:
  - `id`: Admin or Cashier ID
  - `productId`: Product ID
- **Required Body Fields**:
  - `quantity`
  - `finalPrice`

#### 2. **Get Sale by Product ID**
- **Endpoint**: `GET /api/sale/getProductId/:id`
- **Description**: Retrieves sales using the product ID.
- **Required Parameters**:
  - `id`: Admin or Cashier ID
- **Required Field**: `code`

#### 3. **Get All Sales**
- **Endpoint**: `GET /api/sale/:id`
- **Description**: Retrieves all sales associated with the admin or cashier.
- **Required Parameters**:
  - `id`: Admin or Cashier ID

#### 4. **Delete Sale (Return Product)**
- **Endpoint**: `DELETE /api/sale/:id/:saleId`
- **Description**: Deletes a sale record if the product is returned.
- **Required Parameters**:
  - `id`: Admin ID
  - `saleId`: Sale ID
- **Note**: Admin protected middleware required.

### Product Management Endpoints

#### 1. **Create Product**
- **Endpoint**: `POST /api/product/create-product/:id`
- **Description**: Creates a new product.
- **Required Parameters**:
  - `id`: Admin ID
- **Required Body Fields**:
  - `name`
  - `code` (must be unique)
  - `quantity`
  - `price`
  - `category`

#### 2. **Get Total Stock Value**
- **Endpoint**: `GET /api/product/total/:id`
- **Description**: Retrieves the total stock value of materials.
- **Required Parameters**:
  - `id`: Admin ID

#### 3. **Get Out-of-Stock Products**
- **Endpoint**: `GET /api/product/stock/:id`
- **Description**: Retrieves out-of-stock products and sends an email notification when products are low in stock.
- **Required Parameters**:
  - `id`: Admin ID

#### 4. **Get All Products**
- **Endpoint**: `GET /api/product/:id`
- **Description**: Retrieves all product materials.
- **Required Parameters**:
  - `id`: Admin or Cashier ID

#### 5. **Update Product**
- **Endpoint**: `PATCH /api/product/update-product/:id/:productId`
- **Description**: Updates product details.
- **Required Parameters**:
  - `id`: Admin ID
  - `productId`: Product ID
- **Note**: Admin and payment protection required.

#### 6. **Delete Product**
- **Endpoint**: `DELETE /api/product/delete-product/:id/:productId`
- **Description**: Deletes a product from the inventory.
- **Required Parameters**:
  - `id`: Admin ID
  - `productId`: Product ID
- **Note**: Admin and payment protection required.

---

## 💻 Getting Started

### Prerequisites
Before you begin, ensure you have the following installed:
- Node.js (v14 or later)
- npm (Node package manager)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
💻 Getting Started
Prerequisites
Before you begin, ensure you have the following installed:

Node.js (v14 or later)
npm (Node package manager)
Installation
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
Install the dependencies:

bash
Copy code
npm install
Running the Application Locally
To start the application in development mode:

bash
Copy code
npm run dev
The application will be available at http://localhost:3000.

🎉 Contributing
If you'd like to contribute to this project, feel free to fork the repository and submit a pull request. Your contributions are welcome!

📄 License
This project is licensed under the MIT License. See the LICENSE file for details.

