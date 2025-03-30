# Bicycle Tracking Web App Documentation

## Introduction
The Bicycle Tracking Web App is a real-time tracking system that monitors the location, speed, and direction of bicycles. It utilizes Django, WebSockets, and mapping APIs to provide an interactive user experience.

## Features
- **Real-time Updates:** Tracks bicycle location, speed, and direction instantly using WebSockets.
- **Map Integration:** Displays bicycle routes on an interactive map.
- **User Authentication:** Secure login and session management.
- **Data Storage:** Stores historical tracking data for analysis.
- **Notifications:** Alerts for unusual speed or location deviations.

## Technologies Used
- **Backend:** Django, Django Channels (WebSockets)
- **Frontend:** JavaScript, HTML, CSS
- **Database:** PostgreSQL
- **APIs:** Google Maps API / OpenStreetMap, WebSockets

## Installation Guide

### Prerequisites
Ensure you have the following installed:
- Python 3.x
- PostgreSQL
- Node.js (for frontend dependencies)
- Redis (for WebSocket message brokering)

### Setup Steps
1. Clone the repository:
    ```bash
    git clone https://github.com/JPBradley3/bicycle-tracking.git
    cd bicycle-tracking
    ```
2. Create a virtual environment and install dependencies:
    ```bash
    python -m venv env
    source env/bin/activate  # On Windows use: env\Scripts\activate
    pip install -r requirements.txt
    ```
3. Configure the database in `settings.py`:
    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'bicycle_db',
            'USER': 'your_user',
            'PASSWORD': 'your_password',
            'HOST': 'localhost',
            'PORT': '5432',
        }
    }
    ```
4. Apply migrations:
    ```bash
    python manage.py migrate
    ```
5. Start Redis for WebSocket support:
    ```bash
    redis-server
    ```
6. Run the Django development server:
    ```bash
    python manage.py runserver
    ```

## WebSocket Integration

### WebSocket Configuration in Django
Add Django Channels to `INSTALLED_APPS` in `settings.py`:
```python
INSTALLED_APPS = [
    'channels',
    'bicycle_tracking',
]
