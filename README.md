# Forecast API

Hey! So you wanted to check out this project. Here’s the simple breakdown of what it is and how to get it running.

## What is this?

This is a simple backend API that does two main things:

1.  **Manages a list of users:** You can add users, see who's on the list, update their info, and remove them.
2.  **Fetches Weather:** For any user who has a city listed, it can grab the current weather for them using an external service.

It's built with Node.js and Express, and it uses MongoDB to store the user data.

## How to Get it Running (The Quick Way)

Follow these steps and you'll have it running locally in a few minutes.

### 1. Set Up Your Keys

You need two secret keys for this to work.

*   **Create a file named `.env`** in the main project folder.

*   **Copy and paste this into the `.env` file:**

    ```env
    # The address for your local MongoDB database
    MONGODB_URI="mongodb://localhost:27017/my-database"

    # Your API key from OpenWeatherMap
    WEATHER_API_KEY="your_weather_api_key_goes_here"
    ```

*   **Get the Weather Key:**
    *   Go to [OpenWeatherMap](https://openweathermap.org/api), sign up for a free account.
    *   Go to the 'API keys' tab on your account page and copy your key.
    *   Paste that key into the `.env` file where it says `"your_weather_api_key_goes_here"`.

### 2. Install and Run

*   **Open your terminal** in the project folder.
*   **Install the dependencies** (all the code libraries it needs):
    ```bash
    npm install
    ```
*   **Start the server:**
    ```bash
    node server.js
    ```

If everything worked, you'll see a message that says `Server running at http://localhost:3000/`.

## How to Use the API (with Postman)

The easiest way to test the API is with a tool like [Postman](https://www.postman.com/).

### 1. Add a New User

*   **Method:** `POST`
*   **URL:** `http://localhost:3000/users`
*   **Body:** Go to the "Body" tab, select "raw", choose "JSON", and paste this in:

    ```json
    {
        "name": "Your Name",
        "email": "your.email@example.com",
        "city": "Paris"
    }
    ```
*   Hit "Send". You've just created a user!

### 2. Get All Users

*   **Method:** `GET`
*   **URL:** `http://localhost:3000/users`
*   Hit "Send". You should see a list of all the users you've added.

### 3. Get Weather for a User

*   **First, get a user's ID:** After you create a user or get all users, copy the `_id` value from one of them.
*   **Method:** `GET`
*   **URL:** `http://localhost:3000/users/<PASTE_USER_ID_HERE>/weather`
*   Hit "Send". You should get the current weather for that user's city!

### 4. Delete a User

*   **Method:** `DELETE`
*   **URL:** `http://localhost:3000/users/<PASTE_USER_ID_HERE>`
*   Hit "Send". The user will be removed from the database.

That's pretty much it! Let me know if you run into any issues.
