# Course Management System (Servlet-Based)

## Overview
This is a **Course Management System** built with **Java Servlets and JSP**, designed to manage course registrations efficiently. It supports three distinct user roles:

* **Admin:** Manages courses and faculty assignments.
* **Teacher:** Views assigned courses and student lists.
* **Student:** Browse courses by semester and handles enrollment.

The project uses **Java JDK 21** and **Tomcat 11.1.5** for deployment.

---

## Features

### 1. Admin
* Add new courses to the system.
* Assign teachers to specific courses.

### 2. Teacher
* View list of assigned courses.
* View students enrolled in specific courses.

### 3. Student
* Filter and view courses based on semester.
* Enrol in selected courses.
* View a list of currently enrolled courses.

---

## Technology Stack

* **Backend:** Java Servlets, JSP
* **Frontend:** HTML, CSS, JavaScript
* **Database:** MySQL
* **Server:** Apache Tomcat 11.1.5
* **Java Version:** JDK 21
* **Deployment:** WAR file

---

## Database Setup

1.  **Create the database:**
    ```sql
    CREATE DATABASE student_info;
    ```

2.  **Create necessary tables:**
    Run the SQL script provided in `database.sql` to create the following tables:
    * `students`
    * `teachers`
    * `courses`
    * `course_registration`

3.  **Configure Database Connection:**
    Update the `db_connection` properties in your Servlet configuration if necessary:
    ```properties
    URL: jdbc:mysql://localhost:3306/student_info
    User: root
    Password: [your_password]
    ```

---

## Deployment Process (WAR File)

A pre-built WAR file is provided for easy deployment via the Tomcat Manager App.

### Step 1: Start Apache Tomcat
Navigate to your Tomcat installation directory in the terminal/command prompt.

* **On Linux/Mac:**
    ```bash
    ./bin/startup.sh
    ```
* **On Windows:**
    ```cmd
    startup.bat
    ```

*Open a browser and verify Tomcat is running at:* `http://localhost:8080/`

### Step 2: Enable Manager App Access
To deploy WAR files via the GUI, you must enable the `manager-gui` role.

1.  Open `conf/tomcat-users.xml` in your Tomcat directory.
2.  Add the following lines inside the `<tomcat-users>` tag:
    ```xml
    <role rolename="manager-gui"/>
    <user username="admin" password="admin123" roles="manager-gui"/>
    ```
3.  **Restart Tomcat** to apply changes.

### Step 3: Access Tomcat Manager App
1.  Go to: `http://localhost:8080/manager/html`
2.  Log in using the credentials configured in Step 2 (e.g., User: `admin`, Pass: `admin123`).

### Step 4: Deploy WAR File
1.  Scroll down to the **Deploy** section of the Manager page.
2.  Look for **"WAR file to deploy"**.
3.  Click **Choose File** and select your `course_management.war` file.
4.  Click **Deploy**.

*Tomcat will automatically extract and deploy the application.*

### Step 5: Access the Application
Once deployed, the application is accessible at:

**`http://localhost:8080/course_management/`**
