# WEB

A full-stack web application for managing supermarket products, prices, offers, users, and supermarket data.

The project was developed as a web application using **Node.js**, **Express**, **MongoDB/Mongoose**, **EJS**, and **Passport.js**. It provides separate user and administrator functionality, product and category management, supermarket offers, price data, statistics, and a token/points-based contribution system.

## Features

- **User authentication**
  - Registration and login
  - Password hashing with bcrypt
  - Session-based authentication with Passport.js
  - Separate user and administrator access

- **Supermarket & offer management**
  - Browse supermarkets and available offers
  - Add product offers to supermarkets
  - Validate offers against current and historical prices
  - Like/dislike offer functionality
  - Automatic offer expiration and refresh rules

- **Product & category management**
  - Product database
  - Product categories and subcategories
  - Product price history
  - Administrative upload of product, category, price, and supermarket data

- **Price analysis**
  - Daily product prices
  - Weekly average prices
  - Historical price data stored in JSON and MongoDB
  - Comparison of submitted offers with current and average prices

- **Points & token system**
  - Users receive points for contributing valid offers
  - Monthly points are tracked
  - A scheduled process distributes tokens based on user activity

- **Statistics**
  - Offer statistics over time
  - Category and subcategory filtering
  - Weekly discount analysis
  - Administrative statistics pages

- **Geographical data**
  - Supermarket location data
  - GeoJSON data
  - Leaflet support for map-based functionality

## Tech Stack

| Technology | Purpose |
|---|---|
| **Node.js** | Runtime environment |
| **Express.js** | Web server and routing |
| **MongoDB** | Database |
| **Mongoose** | MongoDB ODM |
| **EJS** | Server-side HTML rendering |
| **Passport.js** | Authentication |
| **bcrypt** | Password hashing |
| **Multer** | File uploads |
| **Leaflet** | Interactive maps |
| **Express Session** | User sessions |
| **node-cron** | Scheduled background tasks |
| **CORS** | Cross-origin request handling |
| **Method Override** | HTTP method overrides |

## Project Structure

```text
WEB/
├── categories/              # Uploaded category/subcategory data
├── models/                  # Mongoose database models
├── prices/                  # Uploaded price data
├── products/                # Uploaded product data
├── public/                  # Static frontend assets
├── supermarket/             # Uploaded supermarket data
├── views/                   # EJS templates
├── Data.Prices.json         # Price dataset
├── Data.categ_subcs.json    # Category/subcategory dataset
├── Data.products.json       # Product dataset
├── Data.supermarkets.json   # Supermarket dataset
├── Prices.json              # Historical price data
├── export.geojson           # Geographical data
├── offer-generation.js      # Generates sample offers
├── passport-config.js       # Passport authentication configuration
├── prices.js                # Generates price history data
├── product_prices.js        # Updates product price history
├── server.js                # Main Express application
├── supermarketupload.js     # Supermarket data upload handling
├── user.js                  # User data generation/management
├── package.json             # Project configuration and dependencies
└── README.md
```

## Getting Started

### Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/)
- MongoDB / access to a MongoDB database
- npm

### Installation

Clone the repository:

```bash
git clone https://github.com/Tsomaros/WEB.git
cd WEB
```

Install dependencies:

```bash
npm install
```

### Environment Configuration

Create a `.env` file for local development and configure the required environment variables.

> **Important:** Database credentials and application secrets should not be committed to Git. The current source code contains database configuration that should be moved to environment variables before deploying the application.

### Run the Application

Start the server with:

```bash
npm start
```

The application runs on:

```text
http://localhost:3000
```

## Application Workflow

The application is centered around a database of supermarkets, products, prices, users, and offers.

1. Users authenticate through the login/registration system.
2. Authenticated users can browse supermarkets and products.
3. Users can submit product offers for supermarkets.
4. Submitted offers are checked against stored price information.
5. Valid contributions can award points to the submitting user.
6. Offers are automatically monitored and may be refreshed or removed according to their age and price conditions.
7. Administrators can manage uploaded datasets and access statistics.

## Scheduled Tasks

The server uses **node-cron** for automated tasks, including:

- Resetting monthly user points and adding tokens to the token bank.
- Distributing a portion of the token bank to users based on monthly activity.
- Checking old offers and refreshing or removing them according to the application's rules.

## Data

The repository contains several datasets used by the application, including:

- Product information
- Product categories and subcategories
- Supermarket information
- Historical prices
- Supermarket geographical information
- Example/generated offers

Large JSON datasets are included in the repository to support the application's data-driven functionality.

## Scripts

The main npm script is:

```bash
npm start
```

which executes:

```bash
node server.js
```

Additional JavaScript utilities are included for generating and updating users, prices, products, and offers.

## Security Note

This repository is intended as an academic/development project. Before using it in a production environment:

- Move database connection strings to environment variables.
- Use strong, environment-specific session secrets.
- Do not commit credentials or other sensitive information.
- Review authentication and authorization logic.
- Enable secure cookies and HTTPS in production.
- Validate and sanitize uploaded files and user input.
