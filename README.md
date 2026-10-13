# Student Management System

A simple Django-based Student Management System for managing student records and marks. This repository provides models, admin configuration, and basic frontend templates (HTML) to manage students and their marks.

## Table of Contents
- [About](#about)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Run the Project](#run-the-project)
- [Models](#models)
- [Admin Interface](#admin-interface)
- [Usage Examples](#usage-examples)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About
This application stores student details (roll number, name, department, year, contact info) and their marks per subject (internal/external). The admin interface is configured with inline marks editing for quick management.

## Features
- CRUD operations for students and marks via Django admin
- Inline editing of marks on student admin page
- Search and filters for quick lookup
- Clear model separation between Student and Marks

## Tech Stack
- Python 3.x
- Django (recommended >= 4.x)
- SQLite (default) or any Django-supported database
- HTML templates for frontend

## Project Structure (high-level)
- manage.py
- project_settings/ (your Django project settings)
- app/ (student management app)
  - models.py
  - admin.py
  - views.py
  - templates/
  - static/
- requirements.txt

> Note: Replace the above names with actual directories in your repo if different.

## Requirements
- Python 3.8+
- pip
- (Optional) virtualenv or venv

## Installation
1. Clone the repo:
   git clone https://github.com/kurubavasu23-hash/student_management-_system.git
   cd student_management-_system

2. Create and activate a virtual environment (recommended):
   python -m venv venv
   - On macOS / Linux:
     source venv/bin/activate
   - On Windows:
     venv\Scripts\activate

3. Install dependencies:
   pip install -r requirements.txt
   (If requirements.txt is missing, install Django: pip install django)

4. Apply database migrations:
   python manage.py migrate

5. Create a superuser to access admin:
   python manage.py createsuperuser

## Configuration
- Settings: set `SECRET_KEY`, `DEBUG`, `ALLOWED_HOSTS` and database settings in your Django settings or via environment variables.
- Example environment variables (use a .env or export in your shell):
  SECRET_KEY='your-secret-key'
  DEBUG=True
  ALLOWED_HOSTS=localhost,127.0.0.1

- If using PostgreSQL, add appropriate DATABASES config in settings.py.

## Run the Project
Start development server:
python manage.py runserver

Open http://127.0.0.1:8000/ and admin at http://127.0.0.1:8000/admin/

## Models
This project includes (based on admin configuration):

- Student1
  - roll_number (unique id)
  - full_name
  - department
  - year
  - email
  - phone
  - (other fields may exist in models.py)

- Marks
  - student (ForeignKey -> Student1)
  - subject_code
  - subject_name
  - semester
  - internal_marks
  - external_marks
  - total (computed or stored)
  - grade
  - result

(See app/models.py for exact field names and types.)

## Admin Interface
- Student admin shows fields: roll_number, full_name, department, year, email, phone.
- Marks are shown as inline on the Student admin page for quick entry (TabularInline).
- Marks admin displays: student, subject_code, subject_name, semester, internal_marks, external_marks, Total, grade, result.
- Search fields and filters are configured for convenience.

## Usage Examples
- Add a new student: Admin -> Students -> Add Student
- Add marks inline: Open a Student record and add Marks rows inline (no need to go to Marks separately).
- Search: Use roll number or student name in admin search to quickly find records.

## Testing
Run tests (if provided):
python manage.py test

## Contributing
- Fork the repo.
- Create a topic branch: git checkout -b feat/your-feature
- Make changes and add tests.
- Commit and push: git push origin feat/your-feature
- Create a pull request describing your changes.

Please follow standard Django best practices and keep migrations included where appropriate.

## License
Specify a license (e.g., MIT). If you have no license file, add one (LICENSE) to the repository.

## Contact
Maintainer: kurubavasu23-hash
For questions or suggestions, open an issue in the repository.
