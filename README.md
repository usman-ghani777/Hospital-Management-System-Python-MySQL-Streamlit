---
title: Hospital Management System
emoji: 🏥
sdk: streamlit
app_file: app.py
---

# Hospital Management System

A comprehensive Hospital Management System built using **Python** (Streamlit) and **MySQL**. This application allows for efficient management of hospital records, including patients, doctors, and appointments.

## 🚀 Features

The application provides a user-friendly interface to perform the following operations:

### 🏥 Patient Management
*   **Add Patient**: Register new patients with details like Name, Age, Gender, Diagnosis, and Admission Date.
*   **View Patients**: View a list of all registered patients.
*   **Delete Patient**: Remove patient records (automatically handles linked appointments).

### 👨‍⚕️ Doctor Management
*   **Add Doctor**: Register new doctors with Name, Specialty, and Phone Number.
*   **View Doctors**: View a list of all available doctors.
*   **Delete Doctor**: Remove doctor records (automatically handles linked appointments).

### 📅 Appointment Management
*   **Book Appointment**: Schedule appointments between registered patients and doctors.
*   **View Appointments**: distinct dashboard to view scheduled appointments with details.
*   **Delete Appointment**: Cancel/Remove appointment records.

## 🛠️ Technologies Used
*   **Frontend**: [Streamlit](https://streamlit.io/)
*   **Database**: [MySQL](https://www.mysql.com/)
*   **Language**: Python 3.x
*   **Libraries**: `pandas`, `pymysql`

## ⚙️ Usage & Installation

### 1. Prerequisites
Ensure you have Python and MySQL installed on your system.

### 2. Database Setup
Create a MySQL database named `hospital` and run the following SQL queries to set up the tables:

```sql
CREATE DATABASE hospital;
USE hospital;

-- Table for Patients
CREATE TABLE patients (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    age INT,
    gender VARCHAR(50),
    diagnosis VARCHAR(255),
    admitted_on DATE
);

-- Table for Doctors
CREATE TABLE doctors (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    specialty VARCHAR(255),
    phone VARCHAR(50)
);

-- Table for Appointments
CREATE TABLE appointments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE,
    reason TEXT,
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);
```

### 3. Application Configuration
Update the `config.py` file with your MySQL database credentials:

```python
MYSQL_HOST = 'localhost'
MYSQ_USER = 'root'        # Your MySQL Username
MYSQL_PASSWORD = 'your_password' # Your MySQL Password
MYSQL_DATABASE = 'hospital'
```

### 4. Installation
Install the required Python packages:

```bash
pip install -r requirements.txt
```

### 5. Run the Application
Launch the Streamlit app:

```bash
streamlit run app.py
```

## 📂 Project Structure
*   `app.py`: Main application file containing the Streamlit interface and logic.
*   `db.py`: Database helper functions for CRUD operations.
*   `config.py`: Configuration file for database connection.
*   `requirements.txt`: List of dependencies.
