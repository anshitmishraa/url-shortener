# URL Shrinker

A URL shortening service that allows users to convert long URLs into short, shareable links. This application utilizes MongoDB and Mongoose for data storage and Express.js for routing. Users can generate short URLs, view the full and shortened URLs along with their click counts, and redirect to the original URL upon accessing the shortened version.

## Table of Contents
- [Features](#features)
- [Demo](#demo)
- [Installation](#installation)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [Configuration](#configuration)
- [Customization](#customization)

---

## Features

1. **URL Shortening**: Convert long URLs into shortened versions for easy sharing.
2. **Click Tracking**: Track the number of clicks on each shortened URL.
3. **Dynamic Redirects**: Redirect users from shortened URLs to the original full URL.
4. **Web Interface**: A simple and responsive web interface to create and view short URLs.
5. **Data Persistence**: Store URL data and click counts in MongoDB.

## Demo

Check out the live demo of the URL Shrinker [here](#).

---

## Installation

### Prerequisites

- **Node.js**: Ensure Node.js is installed. Download and install from [Node.js official site](https://nodejs.org/).
- **MongoDB**: Set up a MongoDB instance. You can use [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for a cloud-based database.

### Steps

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/anshitmishraa/url-shrinker.git
    ```

2. **Navigate to Project Directory**:
    ```bash
    cd url-shrinker
    ```

3. **Install Dependencies**:
    ```bash
    npm install
    ```

4. **Set Up Environment Variables**:
   - Create a `.env` file in the root directory of the project.
   - Add the MongoDB connection string:
     ```plaintext
     MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/<dbname>?retryWrites=true&w=majority
     ```

5. **Start the Application**:
    ```bash
    npm start
    ```

6. **Access the Application**:
   - Open your browser and go to `http://localhost:5000`.

---

## Usage

1. **Open the Application**: Navigate to the application URL.
2. **Shrink a URL**:
   - Enter the long URL in the input field and click "Shrink".
   - The shortened URL will be displayed in the table along with the original URL and click count.
3. **Access Shortened URLs**:
   - Click on the shortened URL to be redirected to the original URL.
4. **View Click Counts**:
   - The number of clicks on each shortened URL is updated and displayed in the table.

---

## Code Structure

```
url-shrinker/
│
├── models/
│   └── shortUrl.js          # Mongoose model for URL data
│
├── views/
│   └── index.ejs            # EJS template for the main web interface
│
├── app.js                   # Main application file
├── package.json             # Project metadata and dependencies
├── .env                     # Environment variables (MongoDB URI)
└── README.md                # Documentation
```

### Detailed Explanation

- **`models/shortUrl.js`**:
  - Defines the Mongoose schema and model for storing URLs.
  - Fields:
    - `full`: The original long URL.
    - `short`: The shortened URL, generated using `shortid`.
    - `clicks`: Number of clicks on the shortened URL.

- **`views/index.ejs`**:
  - Provides the front-end layout with a form for URL shortening and a table to display the URLs and click counts.

- **`app.js`**:
  - Contains the Express.js server setup and routing.
  - Routes:
    - `GET /`: Render the main page with all shortened URLs.
    - `POST /shortUrls`: Create a new shortened URL from the provided full URL.
    - `GET /:shortUrl`: Redirect to the original URL and increment the click count.

---

## Configuration

- **MongoDB Connection**:
  - Ensure the `MONGO_URI` in the `.env` file is correctly configured to connect to your MongoDB database.

- **Port Configuration**:
  - The application runs on port 5000 by default. You can change this by setting the `PORT` environment variable.

---

## Customization

1. **Change Short URL Length**:
   - Modify the `shortUrlSchema` in `models/shortUrl.js` if you need a different length for the shortened URLs.

2. **Modify URL Redirection Logic**:
   - Adjust the redirection behavior in the `app.get('/:shortUrl', ...)` route in `app.js`.

3. **Enhance User Interface**:
   - Edit `views/index.ejs` to update the styling or layout of the web interface.

4. **Add More Features**:
   - Implement additional features such as URL expiration, custom short URLs, or user authentication.
