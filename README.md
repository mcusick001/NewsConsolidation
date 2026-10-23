========================================================================
                      DJANGO NEWS API CAPSTONE PROJECT
========================================================================

-------------------
1. PROJECT OVERVIEW
-------------------
This project is a comprehensive full-stack News and Content Management Portal
built with Django and Django REST Framework (DRF), backed by a MariaDB relational
database, fully containerized with Docker and documented using Sphinx. It features 
strict Role-Based Access Control (RBAC), custom web dashboards for readers,
journalists, and editors, automated email notifications, and webhook event handlers.

## GitHub Repository Link
You can access, fork, or clone the physical repository for testing and deployment
from your GitHub profile:
https://github.com/mcusick001/NewsConsolidation.git

-----------------
2. PREREQUISITES
-----------------
Make sure you have the following installed on your system:
 - Python (version 3.14.4)
 - MariaDB / MySQL server

-----------------------------
3. LOCAL SETUP & INSTALLATION
-----------------------------
1. Clone the repository and navigate into the project directory:
   ```bash

      git clone [https://github.com/mcusick001/NewsConsolidation.git]

      cd "Capstone-Project Consolidation"
   ```

2. Set Up a Virtual Environment & Install Dependencies
   ```bash
    
   python -m venv venv

   venv\Scripts\Activate.ps1

   pip install -r requirements.txt
   ```

3. Configure the Environmental Variables
   - Windows (Command Prompt):
   ```cmd

   copy .env.example .env
   ```
   - Open the newly created .env file in your code editor and update
     the database username, password, and secret key to match your
     local environment.

4. Log into your MariaDB shell and create the database:
   ```bash

   mysql -u root -p
   ```
   - Once logged in, run the following SQL commands to create the
     database and user:
   ```sql

   CREATE DATABASE news_db;
   CREATE USER 'db_user'@'localhost' IDENTIFIED BY 'db_password';
   GRANT ALL PRIVILEGES ON news_db.* TO 'db_user'@'localhost';
   FLUSH PRIVILEGES;
   EXIT;
   ``` 

5. Run Database Migrations
   - Apply the Django schema to your MariaDB instance:
   ```bash:

   python manage.py makemigrations
   python manage.py migrate
   ```

-----------------------
4. AUTOMATED TEST SUITE
-----------------------
The project includes a robust unit test suite (`APITestCase`) in `news/tests.py`
covering authentication, RBAC permissions, webhook mocking, and subscription filtering.

To run the automated tests:
   ```bash

   python manage.py test
   ```

------------------------
5. DOCKER IMPLEMENTATION
------------------------
   - Ensure Docker Desktop is running on your machine.
   - From the project root directory, build and launch the containers using Docker
     Compose:
     ```bash

     docker-compose up --build
     ```

   - The application will be accessible at http://localhost:8000 .

----------------
6. DOCUMENTATION
----------------
   - The project documentation is built using Sphinx. You can view the built HTML
     documentation locally by opening: docs/_build/html/index.html in your web
     browser.