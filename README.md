# TTS Announcer

A lightweight Django web application that turns typed text into spoken announcements using the browser's built-in Text-to-Speech (TTS) support.

The app is designed for quick, browser-based voice announcements and includes a simple interface with:

- a text input box for the announcement
- a voice selector
- an announce button
- a stop button

Live demo: https://tts-announcer.onrender.com/announcer/

## Features

- Type any message and speak it aloud
- Choose from available browser voices
- Start and stop speech playback
- Simple deployment-ready Django project
- Static files served correctly via WhiteNoise

## Tech Stack

- Python
- Django 5.0.6
- SQLite
- Gunicorn
- WhiteNoise
- HTML, CSS, and JavaScript

## Project Structure

```text
tts_announcer/
├── announcer/
│   ├── templates/
│   │   └── announcer/
│   │       └── index.html
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── tts_project/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── db.sqlite3
├── manage.py
├── requirements.txt
├── Procfile
├── build.sh
├── LICENSE
├── README.md
└── staticfiles/
```

## How It Works

The app renders a single page from the `announcer` Django app. The page uses the browser's `SpeechSynthesis` API to:

1. collect the text entered by the user,
2. select the requested voice,
3. create a `SpeechSynthesisUtterance`, and
4. play it using `speechSynthesis.speak()`.

This means the announcement quality and available voices depend on the browser and operating system.

## Local Development

### Prerequisites

- Python 3.10+
- pip
- virtual environment support

### Setup

```bash
git clone https://github.com/dinaofnaija/tts_announcer.git
cd tts_announcer
python -m venv .venv
source .venv/bin/activate   # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Then open the app in your browser:

- http://127.0.0.1:8000/announcer/

## Deployment

This project is prepared for deployment on platforms like Render.

Included deployment files:

- `Procfile`
- `build.sh`
- `requirements.txt`

Example web startup command:

```bash
gunicorn tts_project.wsgi
```

The app also includes `whitenoise` to serve static files in production.

## Notes

- Browser speech support varies by browser.
- Some browsers require user interaction before speaking begins.
- The project currently uses SQLite for local development and simple deployment use.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Author

- dinaofnaija
