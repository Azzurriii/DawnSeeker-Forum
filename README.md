# DawnSeeker Forum: A Multi-Knowledge Community Hub

**Author:** Azurriii

**Version:** 1.0.0 (Initial Release)

**Last Updated:** October 26, 2023

## Table of Contents

1.  **Introduction**
2.  **Project Goals & Features**
3.  **Technology Stack**
4.  **Project Structure**
5.  **Setup & Installation**
    *   Frontend Setup
    *   Backend Setup
    *   Database Setup
6.  **Usage**
7.  **API Endpoints** (Example)
8.  **Contributing**
9.  **License**
10. **Future Enhancements & Road Map**
11. **Troubleshooting**
12. **Acknowledgements**
13. **Contact**

## 1. Introduction

DawnSeeker-Forum is a multi-knowledge forum designed to facilitate discussions, knowledge sharing, and community building across various topics. It aims to provide a platform where users can ask questions, offer answers, participate in debates, and connect with others who share similar interests. This project is built with a modern tech stack and aims for a clean, user-friendly interface.

## 2. Project Goals & Features

*   **Primary Goal:** To create a versatile and engaging online forum platform that fosters meaningful conversations and knowledge exchange.
*   **Key Features:**
    *   **User Authentication & Authorization:** Secure user accounts with registration, login, and role-based access control.
    *   **Forum Categories:** Organized categories for different topics (e.g., technology, science, literature, etc.).
    *   **Thread Management:** Ability to create, view, reply, and manage forum threads.
    *   **Real-time Updates:** Real-time notifications and updates using Socket.IO for new posts, replies, and reactions.
    *   **Search Functionality:** Robust search capability to easily find relevant discussions and posts.
    *   **User Profiles:** User profiles with details like posts, reputation, and personal bio.
    *   **Voting/Rating System:** Users can upvote or downvote posts to highlight the most helpful content.
    *   **Rich Text Editor:** Support for rich text formatting for posts and replies (e.g., Markdown support).
    *   **File Uploads:** Ability to upload images and other files to posts.
    *   **Responsive Design:** User experience optimized for all devices (desktop, tablets, and mobile).
    *   **Admin Panel:** A dedicated panel for administrators to manage users, categories, and forum settings.
    *   **Moderation Features:** Tools for moderators to delete or edit inappropriate content and manage user disputes.
    *   **Private Messaging:** Users can send direct messages to other registered users.

## 3. Technology Stack

*   **Frontend:**
    *   **Next.js:** React framework for server-side rendering and building a performant web application.
    *   **Tailwind CSS:** Utility-first CSS framework for fast and responsive styling.
    *   **React Hooks:** For managing application state and side effects.
    *   **Socket.IO Client:** For real-time communication with the backend server.
*   **Backend:**
    *   **NestJS:** Node.js framework for building scalable and maintainable server-side applications.
    *   **Passport.js:** Authentication library for securing API endpoints.
    *   **Socket.IO Server:** For enabling real-time communication with the client.
    *   **Class-Validator:** For request data validation.
    *   **TypeORM:** Object-Relational Mapping for managing the database.
    *   **@nestjs/config**: For managing environment variables.
    *   **@nestjs/jwt**: For generating JWTs for authentication and authorization.

*   **Database:**
    *   **PostgreSQL:** Robust and reliable relational database.
*   **Other Tools:**
    *   **bun:** A fast package manager for Node.js.
    *   **Git:** Version control for source code management.
    *   **Docker** Containerisation for ease of deployment
*   **Testing Framework**:
    *   **Jest**: JavaScript testing framework

## 4. Project Structure

The project directory is structured as follows:

```
dawnseeker-forum/
├── client/         # Frontend code (Next.js)
│   ├── components/
│   ├── pages/
│   ├── public/
│   ├── styles/
│   ├── ...
│   └── package.json
├── server/         # Backend code (NestJS)
│   ├── src/
│   │   ├── auth/
│   │   ├── categories/
│   │   ├── users/
│   │   ├── threads/
│   │   ├── posts/
│   │   ├── common/
│   │   ├── main.ts
│   │   └── ...
│   ├── test/ # Test files
│   ├── nest-cli.json
│   ├── package.json
│   └── tsconfig.json
├── docker-compose.yml
├── .env.example
├── .gitignore
├── README.md
```
**Detailed Explanation**
*   **`client`:** This directory contains all the source code for the frontend application, it includes the folders, components, pages, styles, public and everything else for React App.
*   **`server`:** This directory contains all the source code for the backend API, it includes folders for modules, auths, categories, users, threads, posts, common, etc.
*   **`docker-compose.yml`:**  A file to orchestrate the database and the backend and frontend, to ease local development.
*   **`.env.example`:**  Example environment file, to be copied and renamed to `.env`.
*   **`.gitignore`:** Specifies intentionally untracked files that Git should ignore.
*   **`README.md`:**  This file you are currently reading.
*   **`package.json`:**  Root package file to manage common dependencies and commands.

## 5. Setup & Installation

Follow these steps to set up the project on your local machine:

### 5.1. Frontend Setup

1.  **Navigate to the client directory:**
    ```bash
    cd dawnseeker-forum/client
    ```
2.  **Install dependencies:**
    ```bash
    npm install
    # or
    yarn install
    ```
3. **Setup Environment Variables**:
    Copy `.env.example` to `.env` on the client side and configure the following variables as needed
    ```
    NEXT_PUBLIC_API_BASE_URL=http://localhost:3001
    ```
4.  **Run the development server:**
    ```bash
    npm run dev
    # or
    yarn dev
    ```
    The frontend should be available at `http://localhost:3000`.

### 5.2. Backend Setup

1.  **Navigate to the server directory:**
    ```bash
    cd dawnseeker-forum/server
    ```
2.  **Install dependencies:**
    ```bash
    npm install
    # or
    yarn install
    ```
3.  **Setup Environment Variables**:
    Copy `.env.example` to `.env` on the server side and configure the following variables:
     ```
     DATABASE_URL=postgresql://your_db_user:your_db_password@localhost:5432/your_db_name?schema=public
     JWT_SECRET=your_jwt_secret_key
     PORT=3001
     ```
4. **Run Migrations**:
    Before running the server you will need to run the following command to create the database schema on postgres.
    ```bash
    npm run migration:run
    # or
    yarn migration:run
    ```
5.  **Run the development server:**
    ```bash
    npm run start:dev
    # or
    yarn start:dev
    ```
    The backend API should be available at `http://localhost:3001`.

### 5.3. Database Setup

1.  **Install PostgreSQL:** If you don't have PostgreSQL installed, download and install it from the official website.
2.  **Create a new database:** Using your preferred PostgreSQL client (e.g., `psql`, pgAdmin), create a new database named `your_db_name` or as specified in your `.env` file, make sure to change it on the backend side if needed.
3.  **Configure `.env` file:** Update `DATABASE_URL` in the `.env` file to match your database credentials.
4. **Run Migrations**:
   Before running the server you will need to run the following command to create the database schema on postgres.
    ```bash
    npm run migration:run
    # or
    yarn migration:run
    ```

### 5.4. Running with Docker

If you have Docker installed on your computer, you can use `docker-compose` to quickly run the app and its dependencies. To do so, you'll have to copy the .env.example and rename it to .env, then, update the content with your own values. The docker-compose will make sure to run both backend, frontend and the database. 
1.  **Run with docker:**
     ```bash
    docker-compose up -d
    ```
2. **Verify Deployment**:
    You should be able to access the frontend at [http://localhost:3000](http://localhost:3000) and the backend api at [http://localhost:3001](http://localhost:3001).

## 6. Usage

Once the application is running, you can access it via your web browser. Here’s how to interact with the forum:

1.  **Registration/Login:** Start by registering a new account or logging in using existing credentials.
2.  **Browsing Categories:** Navigate through the available forum categories.
3.  **Creating Threads:** Start a new thread within a specific category to ask a question or initiate a discussion.
4.  **Responding to Threads:** View and reply to existing threads.
5.  **User Profiles:** Check out other user profiles to see their contributions.
6.  **Search:** Use the search functionality to find specific topics or posts.
7.  **Voting:** Upvote helpful posts or downvote unhelpful ones.
8.  **Notifications:** Watch for real-time notifications for new replies and updates.

## 7. API Endpoints (Example)

Here are some example API endpoints provided by the backend.
**User Routes**
*   **`POST /auth/signup`**: Registers a new user
*   **`POST /auth/login`**: Login a user to the system
*   **`GET /users/me`**: Gets the current user logged in to the system
*   **`GET /users/:id`**: Get any user by id

**Category Routes**
*   **`GET /categories`**: Gets all the categories
*   **`POST /categories`**: Creates a new category

**Thread Routes**
*   **`GET /threads`**: Gets all the threads
*   **`POST /threads`**: Creates a new thread
*   **`GET /threads/:id`**: Gets thread by ID
*   **`PATCH /threads/:id`**: Update thread by ID
*   **`DELETE /threads/:id`**: Delete thread by ID

**Post Routes**
*   **`GET /posts`**: Gets all the posts
*   **`POST /posts`**: Creates a new post
*   **`PATCH /posts/:id`**: Update a post by ID
*   **`DELETE /posts/:id`**: Delete post by ID

## 8. Contributing

We welcome contributions to improve DawnSeeker-Forum! Here’s how you can contribute:

1.  **Fork the Repository:** Create a fork of this repository to work on your own changes.
2.  **Create a Branch:** Make a new branch for each feature or bug fix you want to implement.
3.  **Code and Commit:** Implement your changes and commit your code with clear and descriptive commit messages.
4.  **Open a Pull Request:** Once you're done, open a pull request (PR) to merge your branch into the main repository.
5.  **Code Review:** Your changes will be reviewed, and feedback will be provided.
6.  **Merge:** After a successful review, your changes will be merged into the project.
7.  **Keep Branches Up-to-Date:** Make sure to keep your development branch up to date with the main branch.

Please follow the existing coding style and conventions in the project and ensure code is well tested before submitting a PR.

## 9. License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## 10. Future Enhancements & Road Map

*   **User Reputation System:** Implement a point system based on post votes.
*   **More Admin Features:** Add more features to the admin panel to manage the forum.
*   **Mobile App:** Develop mobile applications for iOS and Android.
*   **Integration with External Services:** Connect with services like social media platforms.
*   **Advanced Notification System:** Add notification preferences.
*   **Multi-Language Support** Make the Forum available in different languages

## 11. Troubleshooting

If you encounter any issues, please consult the following tips:

*   **Frontend Issues:**
    *   Verify that you have correctly installed all node modules.
    *   Ensure the backend API is running on the correct port.
    *   Check your browser console for any error messages.
*   **Backend Issues:**
    *   Verify that the database configuration is correct.
    *   Check the server logs for any error messages.
    *   Ensure that all necessary node modules have been correctly installed.
* **Docker Issues:**
    * Verify that the docker service is running.
    * Check docker logs in case of any error.
* **General Issues:**
    * Consult the project's Github issues page for common issues.
    * Make sure that you have followed all the steps on the setup guide.

If you are unable to resolve the issue, please raise an issue on the project’s GitHub repository.

## 12. Acknowledgements

*   Thanks to the creators of Next.js, NestJS, PostgreSQL, Socket.IO, Tailwind CSS and other tools that made this project possible.

## 13. Contact

If you have any questions or suggestions, please contact Azurri at [your email].

---
This is a detailed README, and you should tailor it to your project as you develop it further. Remember to update it as you make changes and add new features!
you should be focus on feature and tech
