# My-Python-Projects
Python Projects
**Bus Ticketing System | Python, Tkinter, MySQL, NumPy, Threading**
🚌 Bus Ticketing System
📌 Project Overview

The Bus Ticketing System is a desktop-based application developed using Python, Tkinter, MySQL, and Threading. The system is designed to manage passenger details, seat availability and ticket booking

A key feature of this project is concurrent seat booking management, where Python threading and database locking mechanisms are used to prevent two users from successfully booking the same seat at the same time.

🎯 **Project Objectives**

The main objectives of the project are:

Automate the bus ticket booking process.
Provide a simple and user-friendly desktop interface.
Manage bus seat and passenger information efficiently.
Display real-time seat availability.
Prevent duplicate seat bookings.
Maintain reliable booking records in MySQL.
Handle concurrent booking requests safely.
Demonstrate Python database connectivity and multithreading concepts.

**Technologies Used**
Technology	Purpose
Python	Application development
Tkinter	Graphical User Interface
MySQL	Database management
mysql.connector	Python-MySQL connectivity
Threading	Concurrent booking operations
Lock / RLock	Thread synchronization
NumPy	Numerical/data processing where required
OOP	Modular application design

**Key Features**
🚌 Bus Management
Add bus details
View available buses
Search buses
Display bus information
Manage available seats

**🎫 Ticket Booking**

Enter passenger information
Select available seats
Book tickets
Generate booking information
Store booking details in MySQL
**💺 Seat Management**

The system maintains seat availability and updates the database after successful booking.

Example:

Seat 1  → Available
Seat 2  → Booked
Seat 3  → Available
Seat 4  → Booked
**🔒 Concurrent Seat Booking**

One of the important technical features of this project is handling concurrent seat booking.

Without proper synchronization, two users could attempt to book the same seat at the same time.

Example Problem
User A ──> Check Seat 10 ──> Available
                              ↓
User B ──> Check Seat 10 ──> Available
                              ↓
                    Both attempt booking
                              ↓
                    Duplicate Booking ❌

The project addresses this using thread synchronization and database row-level locking.

**Database Locking**

A transaction can lock the relevant bus record while checking and updating seat availability:

SELECT avail_seat
FROM Bus_Details
WHERE bus_name = %s
FOR UPDATE;

The booking transaction then updates the seat availability before committing the transaction.

🧵 Threading

Python's threading module is used to simulate or handle multiple booking requests.

Conceptually:

Thread 1 → Passenger A → Seat Booking
Thread 2 → Passenger B → Seat Booking
Thread 3 → Passenger C → Seat Booking

A locking mechanism ensures that critical operations are executed safely.

Example concept:

lock.acquire()

try:
    # Check seat availability
    # Book seat
    # Update database
    # Commit transaction
finally:
    lock.release()

This helps prevent race conditions during concurrent booking operations.

🗄️** MySQL Database**

The application uses MySQL to persist application data.

Example Tables
Bus_Details
     │
     ├── bus_name
     ├── avail_seat

Booking
     │
     ├── booking_id
     ├── customer_name
     ├── gender
     ├── mobile
     ├── bus_name
     ├── seat_booked
     └── booking_time
🔌** MySQL Connectivity**

Python connects to MySQL using mysql.connector.

Example:

import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="busdb"
)

cursor = connection.cursor()

Replace the database credentials with your own local MySQL configuration.

🖥️ Tkinter GUI

The application provides a graphical user interface using Tkinter.

Possible screens include:
