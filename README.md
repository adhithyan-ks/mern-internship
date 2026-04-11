<div align="center">

# 🪑 Urban Woods

### A Full-Stack E-Commerce Platform for Premium Wooden Furniture

[![React](https://img.shields.io/badge/React-19.1-61DAFB?style=for-the-badge&logo=react&logoColor=white)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-Express_5-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose_8-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Vite](https://img.shields.io/badge/Vite-6.3-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vite.dev/)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-3.4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)

<br/>

<img src="Screenshot 2025-06-09 011749 copy.png" alt="Urban Woods — Product Listing Page" width="90%"/>

<br/>

*A modern, responsive MERN stack e-commerce application built during an internship to demonstrate full-stack web development proficiency.*

</div>

---

## 📋 Table of Contents

- [About](#-about)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [API Reference](#-api-reference)
- [Screenshots](#-screenshots)
- [License](#-license)

---

## 📖 About

**Urban Woods** is a full-stack e-commerce web application specializing in premium wooden furniture. Built with the **MERN stack** (MongoDB, Express.js, React.js, Node.js), this project was developed during an internship to gain hands-on experience with modern web development practices.

The application features a complete shopping experience — from browsing and searching products, to managing a shopping cart, to a full admin dashboard for inventory management. It implements secure JWT-based authentication, role-based access control, and a clean, responsive UI built with React 19 and Tailwind CSS.

---

## ✨ Features

### 🛒 Customer Features
- **Product Browsing** — Browse the full catalog with product images, descriptions, and pricing
- **Product Details** — Dedicated detail pages for each product
- **Shopping Cart** — Add, update quantities, and remove items with real-time total calculation
- **User Authentication** — Secure sign-up and sign-in with JWT tokens
- **User Profile** — View and manage account details
- **Responsive Design** — Fully optimized for desktop, tablet, and mobile viewports

### 🔧 Admin Features
- **Product Management** — Full CRUD operations (Create, Read, Update, Delete)
- **Add Products** — Add new products with title, description, price, and image URL
- **Edit Products** — Update existing product details inline
- **Inventory Overview** — View all products in a dedicated admin panel
- **Protected Routes** — Admin pages secured behind authentication middleware

### 🔐 Security
- **JWT Authentication** — Stateless, token-based session management via HTTP-only cookies
- **Password Hashing** — Passwords are hashed using `bcryptjs` before storage
- **Route Protection** — Server-side middleware verifies tokens on every protected request
- **Role-Based Access** — Separate routes and controllers for admin vs. regular user actions

---

## 🛠 Tech Stack

| Layer        | Technology                                                             |
| ------------ | ---------------------------------------------------------------------- |
| **Frontend** | React 19, React Router 7, Tailwind CSS 3, Vite 6                      |
| **Backend**  | Node.js, Express 5                                                     |
| **Database** | MongoDB with Mongoose 8 ODM                                           |
| **Auth**     | JSON Web Tokens (JWT), bcryptjs                                        |
| **Tooling**  | ESLint, PostCSS, Autoprefixer, Nodemon                                 |

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     Client (React + Vite)               │
│  ┌──────────┐  ┌──────────┐  ┌─────────┐  ┌─────────┐ │
│  │  Pages   │  │Components│  │ Context  │  │ Router  │ │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬────┘ │
│       └──────────────┴─────────────┴─────────────┘      │
│                         │  fetch()                      │
└─────────────────────────┼───────────────────────────────┘
                          │ HTTP (REST API)
┌─────────────────────────┼───────────────────────────────┐
│                    Server (Express 5)                    │
│  ┌──────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │  Routes  │→ │ Controllers  │→ │   Middleware      │  │
│  │ /api/*   │  │ (Business    │  │ (verifyUser, JWT) │  │
│  └──────────┘  │  Logic)      │  └──────────────────┘  │
│                └──────┬───────┘                         │
│                       │ Mongoose ODM                    │
└───────────────────────┼─────────────────────────────────┘
                        │
┌───────────────────────┼─────────────────────────────────┐
│                  MongoDB Atlas                          │
│  ┌────────────┐ ┌────────────┐ ┌────────────────────┐  │
│  │   Users    │ │  Products  │ │       Carts        │  │
│  └────────────┘ └────────────┘ └────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
ecom-website/
├── client/                          # React frontend (Vite)
│   ├── public/                      # Static assets
│   ├── src/
│   │   ├── assets/                  # Images & media
│   │   ├── components/
│   │   │   ├── Header.jsx           # Navigation bar
│   │   │   ├── Footer.jsx           # Site footer
│   │   │   └── PrivateRoute.jsx     # Auth-guarded route wrapper
│   │   ├── context/
│   │   │   └── user.context.jsx     # Global user state (React Context)
│   │   ├── pages/
│   │   │   ├── HomePage.jsx         # Product listing (landing page)
│   │   │   ├── AllProducts.jsx      # Browse all products
│   │   │   ├── ProductPage.jsx      # Single product detail view
│   │   │   ├── CartPage.jsx         # Shopping cart management
│   │   │   ├── SignUpPage.jsx       # User registration
│   │   │   ├── SignInPage.jsx       # User login
│   │   │   ├── UserDetails.jsx      # User profile page
│   │   │   ├── AboutPage.jsx        # About the store
│   │   │   ├── AddProductPage.jsx   # Admin: add new product
│   │   │   ├── UpdateProductPage.jsx# Admin: edit existing product
│   │   │   └── AdminAllProductsPage.jsx # Admin: product dashboard
│   │   ├── App.jsx                  # Root component & route definitions
│   │   └── main.jsx                 # Application entry point
│   ├── tailwind.config.js
│   ├── vite.config.js
│   └── package.json
│
├── server/                          # Node.js + Express backend
│   ├── controllers/
│   │   ├── auth.controller.js       # Register, login, logout
│   │   ├── admin.controller.js      # Product CRUD (admin only)
│   │   └── user.controller.js       # Cart operations, product queries
│   ├── models/
│   │   ├── user.model.js            # User schema
│   │   ├── product.model.js         # Product schema
│   │   └── cart.model.js            # Cart schema (linked to User & Product)
│   ├── routes/
│   │   ├── auth.route.js            # /api/auth/*
│   │   ├── admin.route.js           # /api/admin/*
│   │   └── user.route.js            # /api/user/*
│   ├── lib/
│   │   ├── verifyUser.js            # JWT verification middleware
│   │   └── error.js                 # Custom error handler
│   ├── index.js                     # Server entry point
│   └── package.json
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or later
- [MongoDB](https://www.mongodb.com/) (local instance or Atlas cluster)
- [Git](https://git-scm.com/)

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/ecom-website.git
cd ecom-website
```

### 2. Set Up the Backend

```bash
cd server
npm install
```

Create a `.env` file in the `server/` directory:

```env
MONGO_DB=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
```

Start the development server:

```bash
npm run dev
```

The API server will start on `http://localhost:3000`.

### 3. Set Up the Frontend

Open a new terminal:

```bash
cd client
npm install
npm run dev
```

The React development server will start on `http://localhost:5173` (default Vite port).

### 4. Open in Browser

Navigate to `http://localhost:5173` to use the application.

---

## 📡 API Reference

### Authentication — `/api/auth`

| Method | Endpoint    | Description              | Auth Required |
| ------ | ----------- | ------------------------ | :-----------: |
| POST   | `/register` | Create a new user        |      ❌       |
| POST   | `/login`    | Sign in & receive token  |      ❌       |
| POST   | `/logout`   | Clear auth cookie        |      ✅       |

### Admin — `/api/admin`

| Method | Endpoint       | Description             | Auth Required |
| ------ | -------------- | ----------------------- | :-----------: |
| POST   | `/add-product` | Add a new product       |      ✅       |
| PUT    | `/update/:id`  | Update product by ID    |      ✅       |
| DELETE | `/delete/:id`  | Delete product by ID    |      ✅       |

### User — `/api/user`

| Method | Endpoint        | Description              | Auth Required |
| ------ | --------------- | ------------------------ | :-----------: |
| GET    | `/all-products` | Fetch all products       |      ❌       |
| GET    | `/product/:id`  | Fetch product by ID      |      ❌       |
| POST   | `/add-to-cart`  | Add product to cart      |      ✅       |
| GET    | `/cart`         | Get user's cart          |      ✅       |
| DELETE | `/cart/:id`     | Remove item from cart    |      ✅       |

---

## 📸 Screenshots

<div align="center">
<img src="Screenshot 2025-06-09 011749 copy.png" alt="Urban Woods — Home & Product Listing" width="85%"/>
<p><em>Product listing page with add-to-cart functionality</em></p>
</div>

---

## 📄 License

This project is open-source and available for personal and educational use.

---

<div align="center">

**Built with ❤️ using the MERN Stack**

*Developed during an internship to learn and apply modern full-stack web development.*

</div>
