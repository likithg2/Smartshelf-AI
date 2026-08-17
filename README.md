# 🛒 SmartShelf AI

**SmartShelf AI** is an AI-powered inventory management and expiry tracking system designed to help users efficiently manage products, monitor expiry dates, receive timely reminders, and reduce product wastage.

The system combines **inventory management, automated expiry notifications, barcode scanning, analytics, and an AI-powered assistant** into a single web application.

---

## 📌 Problem Statement

Managing products with expiry dates manually can lead to forgotten items, unnecessary purchases, product wastage, and financial losses.

**SmartShelf AI** addresses this problem by maintaining a digital inventory of products, tracking their expiry dates, automatically identifying items that are about to expire, and notifying users before expiry.

---

## 💡 Key Features

### 📦 Inventory Management

* Add, edit, view, and delete inventory items
* Store product name, brand, category, quantity, unit, expiry date, location, and barcode
* Track the current status of each item
* Mark products as consumed
* Search and filter inventory

### ⏰ Expiry Tracking & Reminders

* Automatically track product expiry dates
* Identify products expiring soon
* Automatically mark expired products
* Scheduled background expiry checks
* Generate expiry notifications
* Prevent repeated notifications for the same item

### 🔔 Notifications

* In-app notification management
* Push notifications for upcoming expiries
* Email notification support
* Notification history
* Notification preferences

### 🤖 AI Assistant

SmartShelf includes an AI-powered assistant that can interact with the inventory.

It can:

* Search for products using natural language
* Find products by name or brand
* Search using barcodes
* Identify products expiring within a specified period
* Provide information about stored products
* Answer general inventory-related questions
* Provide recipe and usage suggestions through the AI fallback system

Example queries:

```text
What expires in 7 days?
```

```text
When does my milk expire?
```

```text
Show me products from Nestle.
```

```text
What can I make with products expiring soon?
```

### 📊 Analytics Dashboard

* Inventory statistics
* Category-based analysis
* Expiry-related insights
* Graphical data visualization
* Inventory reports
* Exportable reports

### 📷 Barcode Scanner

* Scan product barcodes
* Use barcode information while searching and managing inventory
* Faster product identification

### 👤 User Authentication

* User registration and login
* Secure password hashing
* JWT-based authentication
* Forgot password functionality
* Password reset functionality
* User-specific inventory data

### 📱 Progressive Web App

The frontend includes PWA functionality, allowing SmartShelf to behave like an installable application on supported devices.

### 🎨 User Interface

* Responsive React interface
* Dashboard-based navigation
* Dark/light theme support
* Interactive modals
* Toast notifications
* Animated UI components

---

## 🏗️ System Architecture

SmartShelf AI follows a **client-server architecture**:

```text
┌─────────────────────────────┐
│        React Frontend       │
│      React + Vite + PWA     │
└──────────────┬──────────────┘
               │
               │ REST API
               ▼
┌─────────────────────────────┐
│       Node.js Backend       │
│          Express.js         │
└──────────────┬──────────────┘
               │
       ┌───────┴────────┐
       │                │
       ▼                ▼
┌─────────────┐   ┌──────────────┐
│   MongoDB   │   │  AI Services │
│  Database   │   │ AI Assistant │
└─────────────┘   └──────────────┘
       │
       ▼
┌─────────────────────────────┐
│ Notifications / Reminders   │
│ Push + Email + Cron Jobs    │
└─────────────────────────────┘
```

---

## 🛠️ Technology Stack

### Frontend

* **React 19**
* **Vite**
* **React Router**
* **Tailwind CSS**
* **Axios**
* **Chart.js**
* **Framer Motion**
* **React Hot Toast**
* **HTML2Canvas**
* **jsPDF**
* **Barcode Scanner**
* **PWA**

### Backend

* **Node.js**
* **Express.js**
* **MongoDB**
* **Mongoose**
* **JWT**
* **bcryptjs**
* **Multer**
* **Nodemailer**
* **Node-Cron**
* **Web Push**
* **Axios**

### AI

* **Google Generative AI / Gemini**
* AI-powered natural-language inventory search
* AI chatbot and recommendation functionality

---

## 📂 Project Structure

```text
SmartShelf-AI/
│
├── backend/
│   ├── src/
│   │   ├── ai/
│   │   │   └── chatbotService.js
│   │   │
│   │   ├── config/
│   │   │   └── db.js
│   │   │
│   │   ├── controllers/
│   │   │   ├── activityController.js
│   │   │   ├── aiController.js
│   │   │   ├── analyticsController.js
│   │   │   ├── authController.js
│   │   │   ├── itemController.js
│   │   │   ├── notificationController.js
│   │   │   ├── reminderController.js
│   │   │   └── settingsController.js
│   │   │
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── utils/
│   │   └── server.js
│   │
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── context/
│   │   ├── css/
│   │   ├── pages/
│   │   ├── utils/
│   │   ├── App.jsx
│   │   └── main.jsx
│   │
│   ├── public/
│   ├── package.json
│   └── vite.config.js
│
└── README.md
```

---

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd SmartShelf-AI
```

---

### 2. Backend Setup

Navigate to the backend directory:

```bash
cd backend
```

Install dependencies:

```bash
npm install
```

Create a `.env` file inside the `backend` directory.

Example:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
FRONTEND_URL=http://localhost:5173

JWT_SECRET=your_jwt_secret

GEMINI_API_KEY=your_gemini_api_key

CRON_SCHEDULE=18 13 * * *
CRON_TZ=Asia/Kolkata
```

Add the required credentials for email and push notifications if those services are enabled in your environment.

Start the backend:

```bash
node src/server.js
```

The backend will run on:

```text
http://localhost:5000
```

Health check:

```text
GET /api/health
```

---

### 3. Frontend Setup

Open another terminal:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

The frontend will normally be available at:

```text
http://localhost:5173
```

---

## 🔐 Environment Variables

Never commit API keys, database credentials, JWT secrets, or email credentials to GitHub.

A typical backend `.env` file may contain:

```env
PORT=5000
MONGO_URI=<MongoDB URI>
FRONTEND_URL=http://localhost:5173
JWT_SECRET=<JWT secret>

GEMINI_API_KEY=<Gemini API key>

CRON_SCHEDULE=18 13 * * *
CRON_TZ=Asia/Kolkata
```

Add `.env` to `.gitignore`.

---

## 🔄 Application Workflow

```text
User
 │
 ▼
React Frontend
 │
 ├── Authentication
 ├── Inventory Management
 ├── Barcode Scanner
 ├── Dashboard
 ├── Analytics
 ├── Notifications
 └── AI Assistant
 │
 ▼
Express REST API
 │
 ├── Authentication API
 ├── Inventory API
 ├── Analytics API
 ├── Notification API
 ├── Reminder API
 ├── Activity API
 ├── Settings API
 └── AI Search / Chat API
 │
 ▼
MongoDB
 │
 └── Stores user and inventory data
```

The backend also runs scheduled jobs that check expiry dates and generate notifications for products approaching their expiry date.

---

## 🤖 AI Search Architecture

SmartShelf uses a database-first approach for inventory-related AI queries.

```text
User Query
    │
    ▼
AI Search API
    │
    ├── Detect expiry-related intent
    │
    ├── Search barcode
    │
    ├── Search product name
    │
    ├── Search brand
    │
    └── Partial text matching
    │
    ▼
SmartShelf MongoDB
    │
    ├── Matching Item
    │
    └── Matching Items
    │
    ▼
Formatted Response
```

If an inventory query cannot be resolved through the SmartShelf database, the chatbot can fall back to the configured LLM service for general questions, suggestions, and recommendations.

---

## ⏱️ Automated Expiry Monitoring

SmartShelf uses **Node-Cron** to periodically check inventory.

The scheduled process:

1. Checks products whose expiry date has passed.
2. Updates their status to expired.
3. Finds active products expiring within the configured period.
4. Creates notifications.
5. Sends push notifications.
6. Attempts email notification when configured.
7. Marks notified items to avoid unnecessary duplicate alerts.

This allows expiry monitoring to continue without requiring the user to manually check the dashboard every day, because apparently humans have better things to forget.

---

## 📊 Main Modules

| Module            | Description                             |
| ----------------- | --------------------------------------- |
| Authentication    | Registration, login, password recovery  |
| Inventory         | Product CRUD and inventory tracking     |
| Expiry Management | Expiry detection and status updates     |
| Reminders         | User-configured product reminders       |
| Notifications     | Push and email notifications            |
| Barcode Scanner   | Barcode-based product identification    |
| Analytics         | Inventory statistics and visual reports |
| AI Search         | Natural-language inventory search       |
| AI Chatbot        | Conversational inventory assistant      |
| Activity Log      | Tracks user activities                  |
| Settings          | User preferences and configuration      |

---

## 🔒 Security

The application implements several security mechanisms:

* Password hashing using **bcryptjs**
* JWT-based authentication
* Authentication middleware
* Protected API routes
* CORS configuration
* Environment variables for sensitive credentials
* User-specific database queries
* Server-side validation and error handling

Sensitive credentials should always be stored in environment variables rather than source code.

---

## 🚀 Production Considerations

Before deploying SmartShelf AI to production:

* Configure a production MongoDB database.
* Use a strong randomly generated JWT secret.
* Configure production frontend and backend URLs.
* Store API keys securely.
* Configure HTTPS.
* Configure production email credentials.
* Configure Web Push credentials.
* Review CORS allowed origins.
* Configure an appropriate cron schedule and timezone.
* Build the frontend using:

```bash
npm run build
```

---

## 🔮 Future Enhancements

Potential future improvements include:

* 📱 Native Android/iOS application
* 📸 AI-powered product recognition from images
* 🧾 OCR-based automatic inventory entry from receipts
* 📈 Predictive consumption analysis
* 🛍️ Smart restocking recommendations
* 🧠 Personalized inventory recommendations
* 📊 Advanced waste and cost analytics
* 👨‍👩‍👧 Shared household inventories
* 🔗 Integration with online grocery platforms
* 🌐 Multi-language AI assistant
* 🔔 More granular notification scheduling

---

## 🎯 Objectives

The main objectives of SmartShelf AI are to:

* Reduce product wastage caused by missed expiry dates.
* Help users maintain an organized digital inventory.
* Provide timely expiry reminders.
* Reduce unnecessary repurchasing.
* Improve inventory visibility through analytics.
* Simplify inventory search using natural language.
* Use AI to provide intelligent product-related assistance.

---

## 🌱 Impact

SmartShelf AI promotes efficient resource utilization by helping users identify and consume products before they expire.

The system can help reduce:

* Food and product wastage
* Unnecessary purchases
* Missed expiry dates
* Manual inventory tracking effort
* Household inventory management overhead

---

## 👨‍💻 Development

### Frontend

```bash
cd frontend
npm install
npm run dev
```

### Backend

```bash
cd backend
npm install
node src/server.js
```

### Frontend Production Build

```bash
npm run build
```

---

## 📜 License

This project is developed for educational and project purposes.

---

## ⭐ SmartShelf AI

**Track smarter. Waste less. Manage better. 🤖📦**
