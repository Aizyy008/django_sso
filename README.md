# Django Application with Social SSO Integration (Google, GitHub, Facebook)

This Django project demonstrates how to integrate **Single Sign-On (SSO)** using **Google**, **GitHub**, and **Facebook** as authentication providers. It uses the `social-auth-app-django` package to manage OAuth2 workflows and streamline user login through widely-used platforms.

---

## Features

* User authentication via:

  * Google OAuth2
  * GitHub OAuth2
  * Facebook OAuth2
* Secure login and logout system
* User session management with Django’s built-in authentication
* Clean and extendable structure
* Optional customization of user models

---

## Tech Stack

* Python 3.x
* Django 4.x
* social-auth-app-django
* SQLite (can be replaced with PostgreSQL/MySQL)
* Optional: Bootstrap or other CSS frameworks

---

## Project Structure

```
sso_project/
├── accounts/             # App for handling auth views (optional)
├── sso_project/          # Main Django project configuration
├── templates/            # Login and redirection pages
├── static/               # CSS and JS files
└── manage.py
```

---

## SSO Provider Configuration

Register your app to get client credentials:

* [Google Developer Console](https://console.developers.google.com)
* [GitHub Developer Settings](https://github.com/settings/developers)
* [Facebook for Developers](https://developers.facebook.com)

In `settings.py`:

```python
SOCIAL_AUTH_GOOGLE_OAUTH2_KEY = 'your-google-client-id'
SOCIAL_AUTH_GOOGLE_OAUTH2_SECRET = 'your-google-client-secret'

SOCIAL_AUTH_GITHUB_KEY = 'your-github-client-id'
SOCIAL_AUTH_GITHUB_SECRET = 'your-github-client-secret'

SOCIAL_AUTH_FACEBOOK_KEY = 'your-facebook-app-id'
SOCIAL_AUTH_FACEBOOK_SECRET = 'your-facebook-app-secret'
```

Also update:

```python
INSTALLED_APPS = [
    ...
    'social_django',
    ...
]

AUTHENTICATION_BACKENDS = (
    'social_core.backends.google.GoogleOAuth2',
    'social_core.backends.github.GithubOAuth2',
    'social_core.backends.facebook.FacebookOAuth2',
    'django.contrib.auth.backends.ModelBackend',
)

MIDDLEWARE = [
    ...
    'social_django.middleware.SocialAuthExceptionMiddleware',
    ...
]

LOGIN_URL = 'login'
LOGOUT_URL = 'logout'
LOGIN_REDIRECT_URL = 'home'
```

---

## How to Run the Project

```bash
# Clone the repository
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Apply migrations
python manage.py migrate

# Start the development server
python manage.py runserver
```


