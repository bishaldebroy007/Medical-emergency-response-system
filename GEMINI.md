# Medical EmergenSee Response System (MERS)

## Project Overview
MERS (Medical EmergenSee Response System) is a comprehensive web-based platform designed to integrate various hospital management and emergency response processes. It serves as an intelligent information system to assist in medical decision-making and operational efficiency.

The project is structured as a collection of semi-independent modules, each handling a specific aspect of medical services.

## Architecture & Technology Stack
- **Backend:** PHP (using both `mysqli` and `PDO` extensions).
- **Frontend:** HTML5, CSS3 (Bootstrap 4), JavaScript (jQuery), and Sass.
- **Database:** MySQL / MariaDB.
- **Components:**
  - **HMIS (Hospital Management Information System):** Located in `backend/admin` and `backend/doc`.
  - **Blood Donation Management:** Located in `blood-donation`.
  - **Fundraiser/Sponsorship System:** Located in `fund`.

## Project Structure
- `/assets`: Global CSS, JS, fonts, and images.
- `/backend/admin`: Administrator panel for managing employees, patients, records, and inventory.
- `/backend/doc`: Specialist/Doctor panel for patient care, lab results, and prescriptions.
- `/blood-donation`: Module for donor registration and blood request management.
- `/fund`: Module for managing sponsorships and fundraising.
- `/all DATABASE FILE`: Contains SQL export files for initializing the system.

## Setup and Installation

### Prerequisites
- A PHP environment (e.g., XAMPP, WAMP, or a standalone LAMP/LEMP stack).
- MySQL or MariaDB server.

### Database Setup
This project requires **three separate databases** to be created and initialized:

1.  **HMIS Database:**
    - Create a database named `hmisphp`.
    - Import `all DATABASE FILE/hmisphp.sql`.
2.  **Blood Donation Database:**
    - Create a database named `blood_donation`.
    - Import `all DATABASE FILE/blood_donation.sql`.
3.  **Fundraiser Database:**
    - Create a database named `mydatabase`.
    - Import `all DATABASE FILE/mydatabase.sql`.

### Configuration
Database connection settings are hardcoded in the following files. Update them with your local database credentials if they differ from the defaults (Host: `localhost`, User: `root`, Password: ``):

- `backend/admin/assets/inc/config.php`
- `backend/doc/assets/inc/config.php`
- `blood-donation/connection.php`
- `fund/connection.php`

## Development Conventions
- **Code Organization:** Each module maintains its own `assets/inc` folder for reusable components like navigation, sidebars, and database configurations.
- **Authentication:** Managed via PHP sessions. Administrator passwords are double-hashed using `sha1(md5($password))`.
- **Styling:** The project uses a mix of pre-compiled CSS and Sass. Custom styles should ideally be modified in the `assets/sass` directory and recompiled.
- **Security:** Prepared statements are used in the HMIS modules (`mysqli->prepare`) to prevent SQL injection.

## Usage & Login
The root `index.php` provides a landing page with links to all major modules. 
- **Administrator Login:** `admin@mail.com` / `Password@123`
- **Doctor Login:** Refer to `01 LOGIN DETAILS & PROJECT INFO.txt` for specific IDs and passwords.
