# Simple Console-Based Ticket Booking System

## 🌟 Overview

This is a basic, in-memory **Ticket Booking System** implemented in Java. It allows users to register, book travel tickets, view their journeys, and manage (cancel or modify) their bookings. The application runs entirely from the console and uses Java's `ArrayList` to store user and ticket data in memory (data is not persisted after the application closes).

## ✨ Features

The system offers a comprehensive set of functions accessible via a main menu:

1.  **Create User:** Register a new user with a unique ID, name, email, mobile number, and gender.
2.  **Show Users:** Display the details of all registered users.
3.  **Book Ticket:** Book a new ticket for a registered user, specifying the travel distance, boarding/destination points, and seat number. The ticket cost is automatically calculated (Distance * ₹2).
4.  **Show Journey Details:** Find and display the full details of a specific ticket, including the user who booked it.
5.  **Search Tickets By User ID:** List all tickets booked by a specific user.
6.  **Change Boarding Point:** Modify the boarding point for a ticket owned by a user.
7.  **Cancel Ticket:** Remove a ticket from both the user's list and the global ticket list.
8.  **Delete Account:** Permanently delete a user account and **cascade-delete** all tickets booked by that user.
9.  **Exit:** Terminate the application.

## 🏗️ Project Structure

The system is organized into distinct packages for clear separation of concerns:

| Package | Purpose | Key Classes |
| :--- | :--- | :--- |
| `com.myApp` | Core application logic and state management. | `TicketBooking` (manages lists of all Users and all Tickets) |
| `com.myUser` | Data model for a user, including their personal list of tickets. | `User` |
| `com.myticket` | Data model for a single ticket, including cost calculation and booking user ID. | `Ticket` |
| `com.user_interface` | The entry point and console interaction layer. | `TicketBookingMainClass` |

## 🚀 Getting Started

### Prerequisites

* **Java Development Kit (JDK)** (Version 8 or newer recommended).

### How to Run

1.  **Clone the Repository:**
    ```bash
    git clone [YOUR_GITHUB_REPO_URL]
    cd [your-repo-name]
    ```
2.  **Open in Eclipse:**
    * Open Eclipse and select `File > Import...`.
    * Choose `General > Existing Projects into Workspace` and select the cloned directory.
3.  **Run the Main Class:**
    * Navigate to `src/com.user_interface/TicketBookingMainClass.java`.
    * Right-click the file and choose `Run As > Java Application`.

The application will start, displaying the menu prompts in the console.

## 📝 Example Flow

1.  **Create User:** Enter `1`. Provide ID `101`, Name `Alice`.
2.  **Book Ticket:** Enter `3`. Enter User ID `101`. Enter Distance `100`, Boarding `CityA`, Destination `CityB`, Seat `5`.
    * (Cost will be ₹200)
3.  **Show Journey:** Enter `4`. Enter the Ticket ID generated in the previous step.
4.  **Cancel Ticket:** Enter `7`. Enter User ID `101` and the Ticket ID.
5.  **Exit:** Enter `9`.

## ⚙️ Key Implementation Details

* **In-Memory Storage:** All data (`users` and `tickets` lists in `TicketBooking.java`) is stored in memory and is **non-persistent**.
* **Unique IDs:** Both `User` and `Ticket` objects are identified by unique IDs. The `Ticket` ID is generated randomly upon creation.
* **Dual Tracking:** Tickets are tracked in two places:
    1.  A **global list** in `TicketBooking` for easy searching by Ticket ID.
    2.  A **per-user list** inside the `User` object to link tickets directly to the owner.
    * Methods like `cancelTicket` and `deleteAccount` ensure data consistency by removing tickets from **both** lists.