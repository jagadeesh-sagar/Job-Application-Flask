
# Job Application Form - Flask Web Application

This project is a web-based job application form built using Flask, SQLAlchemy, and Bootstrap. The form allows users to submit their personal and job-related details, which are then stored in a SQLite database. An email confirmation is sent to the user upon successful form submission.

## Features

- Job application form with fields for first name, last name, email, available start date, and occupation.
- Data persistence using SQLite and SQLAlchemy.
- Email notifications using Flask-Mail.
- Frontend styling with Bootstrap 5.
- Flash messages to provide feedback on successful submission.
  
## Prerequisites

Make sure you have the following installed on your system:

- Python 3.x
- Flask
- Flask-SQLAlchemy
- Flask-Mail
- SQLite

You can install the required Python packages using `pip`:

```bash
pip install flask flask-sqlalchemy flask-mail
```

## Project Structure

```
/project-folder
│
├── app.py               # Main application file
├── data.db              # SQLite database
├── templates/
│   └── index.html       # HTML form template
└── README.md            # This file
```

## Configuration

### Mail Setup

To send email notifications, Flask-Mail needs to be configured with valid SMTP credentials. In this example, Gmail is used as the SMTP server.

Add the following environment variables to your system:

- `GMAIL`: Your Gmail address.
- `FLASKFORM`: Your Gmail app password (you may need to set up [App Passwords](https://support.google.com/accounts/answer/185833) for Gmail).

Alternatively, you can hardcode these values in the `app.config` dictionary in `app.py`, but this is not recommended for production.

```python
app.config["MAIL_USERNAME"] = os.getenv("GMAIL")
app.config["MAIL_PASSWORD"] = os.getenv("FLASKFORM")
```

### SQLAlchemy

This app uses SQLite as the database. By default, it stores the data in a file named `data.db` in the project directory. You don't need any configuration for SQLite.

## Running the Application

1. Make sure you are in the project directory.
2. Run the Flask app:

   ```bash
   python app.py
   ```

   The app will be available at `http://localhost:5001/`.

## Database Setup

The database will be automatically created when the application is run for the first time. If you want to manually create the database tables, run the following commands in the Python shell:

```python
from app import db
db.create_all()
```

## Form Submission

Once the form is submitted, the user's data is stored in the database, and they will receive a confirmation email with the details of their submission.

## Flash Messages

After successful form submission, a flash message will appear on the page informing the user of their successful submission.

## Future Improvements

- Add validation for email format.
- Implement more robust error handling.
- Improve frontend styling.
- Add CAPTCHA to prevent spam submissions.

