# Project Overview

This project consists of a backend API and a frontend interface to display and interact with product transactions. The application allows users to view transaction data, statistics, bar charts, and pie charts for any selected month, fetched from a third-party API and stored in a database.

---

## Backend Implementation

### Technologies Used

- Node.js
- Express
- MongoDB (with Mongoose)
- Axios

### Features

#### 1. Initialize Database

- API to fetch seed data from the third-party URL and populate the MongoDB database.
- Clears existing data before seeding new data.

**Endpoint:** `GET /api/initialize`

#### 2. List Transactions

- Supports pagination and search.
- Filters by month regardless of the year.

**Endpoint:** `GET /api/transactions`

**Query Parameters:**

- `month` (required)
- `page` (default: 1)
- `perPage` (default: 10)
- `search` (optional)

#### 3. Statistics API

- Provides the total sale amount, total sold items, and total not sold items for a selected month.

**Endpoint:** `GET /api/statistics`

**Query Parameter:**

- `month` (required)

#### 4. Bar Chart API

- Returns the number of items in specific price ranges for a selected month.

**Endpoint:** `GET /api/bar-chart`

**Query Parameter:**

- `month` (required)

#### 5. Pie Chart API

- Returns unique categories and the number of items per category for a selected month.

**Endpoint:** `GET /api/pie-chart`

**Query Parameter:**

- `month` (required)

#### 6. Combined API

- Fetches and combines data from the Statistics, Bar Chart, and Pie Chart APIs.

**Endpoint:** `GET /api/combined`

**Query Parameter:**

- `month` (required)

### Database Schema

The MongoDB schema for transactions:

```javascript
const transactionSchema = new mongoose.Schema({
    title: String,
    description: String,
    price: Number,
    dateOfSale: Date,
    sold: Boolean,
    category: String,
});
```

---

## Frontend Implementation

### Technologies Used

- React.js
- Axios
- Chart.js

### Features

#### 1. Dropdown for Month Selection

- Displays months from January to December.
- Default selection: March.

#### 2. Transactions Table

- Fetches and displays transaction data for the selected month.
- Supports search functionality to filter transactions by title, description, or price.
- Includes pagination controls (Next/Previous).

#### 3. Statistics Box

- Displays total sale amount, total sold items, and total not sold items for the selected month.

#### 4. Bar Chart

- Visualizes the number of items in various price ranges for the selected month.

#### 5. Pie Chart

- Displays unique categories and the number of items in each category for the selected month.

### State Management

- `useState` and `useEffect` hooks to manage state and fetch data from APIs dynamically.

---

## Installation and Setup

### Backend

1. Clone the repository.
2. Navigate to the backend directory and install dependencies:

   ```bash
   npm install
   ```

3. Create a `.env` file to configure the MongoDB URI:

   ```env
   MONGO_URI=<your_mongodb_connection_string>
   ```

4. Start the backend server:

   ```bash
   npm start
   ```

5. Initialize the database:

   - Visit `http://localhost:5000/api/initialize` in your browser or API client.

### Frontend

1. Navigate to the frontend directory and install dependencies:

   ```bash
   npm install
   ```

2. Start the development server:

   ```bash
   npm start
   ```

3. Open the application in your browser at `http://localhost:3000`.

---

## Usage

1. **Initialize Database**:

   - Seed the database by visiting the `/api/initialize` endpoint.

2. **Access Transactions**:

   - Use the dropdown to select a month.
   - View and interact with transactions in the table (search, pagination).

3. **View Statistics**:

   - Check the total sale amount, sold items, and not sold items in the Statistics Box.

4. **View Charts**:

   - Observe transaction data visually in the Bar and Pie charts.

---

## Future Enhancements

1. Add user authentication.
2. Implement caching for frequently accessed data.
3. Add export functionality for transaction data.
4. Improve UI/UX with advanced styling and responsiveness.

