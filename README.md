# 🚌 Bus Ticket Reservation System (Java + MySQL + HTML/CSS)

## 📌 Project Overview  
The **Bus Ticket Reservation System** is a **simple Java-based** project for booking bus tickets.  
- **Backend:** Java (JDBC - No APIs, No Servlets)  
- **Database:** MySQL  
- **Frontend:** HTML + CSS  
- **Web Server:** Apache Tomcat (for serving JSP pages)

### ✅ Features:
- User Registration & Login (JDBC + MySQL)
- Bus List & Ticket Booking System
- View My Tickets
- Simple Web Interface (HTML, CSS) - No API or React.js

---

## 📂 **Project Folder Structure**
```
📦 Bus-Ticket-Reservation
 ├── 📂 database
 │   ├── bus_reservation.sql      # SQL script to create tables
 ├── 📂 src (Java Backend)
 │   ├── DBConnection.java        # Database connection (JDBC)
 │   ├── User.java                # User registration & login logic
 │   ├── TicketBooking.java       # Ticket booking logic
 │   ├── Main.java                # Main CLI program
 ├── 📂 WebContent (Frontend)
 │   ├── 📂 css
 │   │   ├── style.css            # CSS file for UI styling
 │   ├── 📂 pages
 │   │   ├── index.html           # Home Page
 │   │   ├── login.html           # Login Page
 │   │   ├── register.html        # User Registration Page
 │   │   ├── book_ticket.html     # Ticket Booking Page
 │   │   ├── view_tickets.html    # View Booked Tickets Page
 │   ├── web.xml                  # Servlet configuration (if needed)
 ├── 📂 lib                      # Place MySQL Connector JAR (`mysql-connector-java.jar`)
 ├── README.md                    # Project documentation
```

---

## **🚀 1️⃣ Prerequisites**  
1️⃣ **Install Java JDK 17+** → [Download Java JDK](https://jdk.java.net/java-se-ri/)  
2️⃣ **Install MySQL Server + MySQL Workbench** → [Download](https://dev.mysql.com/downloads/installer/)  
3️⃣ **Install Apache Tomcat** ([Download](https://tomcat.apache.org/download-90.cgi))  
4️⃣ **Download MySQL Connector JAR** ([Download](https://dev.mysql.com/downloads/connector/j/))  
   - Place `mysql-connector-java.jar` inside the `lib/` folder.  

---

# **📌 2️⃣ Database Setup**

1️⃣ Open **MySQL Workbench** or **MySQL Command Line**  
2️⃣ Run the following SQL commands to **create the database & tables**:  
```sql
CREATE DATABASE bus_reservation;
USE bus_reservation;

-- Users Table
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL
);

-- Buses Table
CREATE TABLE buses (
    id INT AUTO_INCREMENT PRIMARY KEY,
    bus_name VARCHAR(100),
    source VARCHAR(100),
    destination VARCHAR(100),
    total_seats INT
);

-- Tickets Table
CREATE TABLE tickets (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    bus_id INT,
    travel_date DATE,
    seat_number INT,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (bus_id) REFERENCES buses(id)
);

-- Sample Bus Data
INSERT INTO buses (id, bus_name, source, destination, total_seats) 
VALUES 
(1, 'Express Bus', 'City A', 'City B', 40),
(2, 'Night Rider', 'City B', 'City C', 50),
(3, 'Fast Track', 'City A', 'City D', 45);
```

---

# **🔧 3️⃣ Running the Backend (Java)**

1️⃣ **Compile Java Files**
```sh
javac -d bin -cp "lib/mysql-connector-java.jar" src/*.java
```

2️⃣ **Run the Program**
```sh
java -cp "bin;lib/mysql-connector-java.jar" Main
```

---

# **🌐 4️⃣ Running the Web Interface (HTML/CSS)**

1️⃣ Install & start **Apache Tomcat**  
2️⃣ Move `WebContent/` into **Tomcat's `webapps/` directory**  
3️⃣ Start Tomcat  
4️⃣ Open **`http://localhost:8080/WebContent/pages/index.html`** in a web browser.  

---

# **💡 Need Help?**
If you face issues, feel free to open a GitHub **issue** or ask here! 😊🚀
