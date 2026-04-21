# Medical EmergenSee Response System (MERS)

A modular web platform that integrates hospital management, blood donation, and fundraising workflows to support clinical decision-making and operational efficiency.

---

## Overview

**MERS** Medical EmergenSee Response System is a web based information system composed of semi independent modules. Each module focuses on a specific hospital or emergency response function while sharing common assets and conventions to simplify deployment and maintenance.

**Key capabilities**
- **Hospital Management Information System** for administrators and doctors  
- **Blood donation** registration and request handling  
- **Fundraiser and sponsorship** management  
- **Role based access** and session driven authentication  
- **Prepared statements** and mixed use of mysqli and PDO for database access

---

## Features

- Administrator panel for employee management, patient records, and inventory  
- Doctor panel for patient care, lab results, and prescriptions  
- Donor registration and blood request workflows  
- Fundraiser and sponsorship management with donation tracking  
- Shared global assets for consistent styling and scripts  
- SQL export files for quick database initialization

---

## Architecture and Technology Stack

**Backend**
- **Language** PHP  
- **Database APIs** mysqli and PDO

**Frontend**
- **Markup and Styling** HTML5 CSS3 Bootstrap 4 Sass  
- **Client scripting** JavaScript jQuery

**Database**
- **Engine** MySQL or MariaDB

**Modules**
- **HMIS** backend/admin and backend/doc  
- **Blood Donation** blood-donation  
- **Fundraiser** fund

---

## Project Structure

**Top level folders**
- **assets** Global CSS JS fonts and images  
- **backend/admin** Administrator panel for employees patients records and inventory  
- **backend/doc** Doctor panel for patient care lab results and prescriptions  
- **blood-donation** Donor registration and blood request management  
- **fund** Sponsorship and fundraising management  
- **all DATABASE FILE** SQL export files for initializing databases

**Module conventions**
- Each module contains an assets/inc folder for reusable components such as navigation sidebars and DB config  
- Authentication is session based  
- Administrator passwords are double hashed using sha1 md5

---

## Database Setup

Create and initialize three separate databases. Import the corresponding SQL files from the all DATABASE FILE folder.

| **Database Name** | **Purpose** | **SQL Import File** |
|---|---|---|
| hmisphp | HMIS module | all DATABASE FILE/hmisphp.sql |
| blood_donation | Blood donation module | all DATABASE FILE/blood_donation.sql |
| mydatabase | Fundraiser module | all DATABASE FILE/mydatabase.sql |

**Example MySQL import commands**
```bash
mysql -u root -p hmisphp < "all DATABASE FILE/hmisphp.sql"
mysql -u root -p blood_donation < "all DATABASE FILE/blood_donation.sql"
mysql -u root -p mydatabase < "all DATABASE FILE/mydatabase.sql"
```

---

## Configuration

Update database connection settings if your environment differs from the defaults Host localhost User root Password empty.

**Files to update**
- backend/admin/assets/inc/config.php  
- backend/doc/assets/inc/config.php  
- blood-donation/connection.php  
- fund/connection.php

Make sure file permissions allow the web server to read these files but do not expose them publicly.

---

## Installation Steps

1. Place the project folder in your web server document root such as htdocs or www.  
2. Create the three databases and import the SQL files as shown in the Database Setup section.  
3. Update the configuration files with your database credentials.  
4. Start Apache and MySQL services.  
5. Open the root index.php in your browser to access the landing page and module links.

---

## Development Conventions

- **Code organization** Modules are semi independent and keep their own assets/inc components  
- **Styling** Modify Sass files in assets/sass and recompile to update custom styles  
- **Database access** HMIS modules use prepared statements to mitigate SQL injection other modules use a mix of mysqli and PDO  
- **Authentication** PHP sessions with admin passwords stored as sha1 md5  
- **Assets** Shared assets live in assets to avoid duplication

---

## Security Notes and Recommendations

**Current practices**
- Prepared statements used in HMIS modules  
- Passwords are double hashed with sha1 md5

**Recommended improvements**
- Replace sha1 md5 with password_hash and password_verify for stronger hashing  
- Centralize database configuration and use environment variables for credentials  
- Enforce HTTPS in production and set secure session cookie flags  
- Validate and sanitize all user inputs server side and client side  
- Implement role based access control checks on every protected endpoint

---

## Usage and Login

- The root index.php is a landing page linking to all modules  
- **Administrator Login**  
  - **Email** admin@mail.com  
  - **Password** Password@123  
- **Doctor Login** See the file named 01 LOGIN DETAILS & PROJECT INFO.txt for doctor credentials and sample accounts

---

## Troubleshooting

- **Blank pages or PHP errors** Enable display_errors during development or check the web server error log  
- **Database connection failures** Verify credentials in the configuration files and ensure the MySQL service is running  
- **Missing assets or broken styles** Confirm the assets folder is accessible and that compiled CSS exists recompile Sass if necessary

---

## Contributing

- Fork the repository create a feature branch and open a pull request with a clear description of changes  
- Follow existing code conventions and keep module changes isolated when possible  
- Add SQL migrations or seeders for schema changes and document required database updates in the pull request

---

## License

[MIT](LICENSE.md)

---

## Contact

For questions about setup deployment or module integration include maintainer contact information or open an issue in the project repository.

---

## Quick Checklist for Developers Before Deployment

- Replace weak password hashing with password_hash  
- Move database credentials to environment variables  
- Enable HTTPS and secure session cookies  
- Test each module independently after database import

---