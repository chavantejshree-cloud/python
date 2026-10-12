# Flask Python Application

## 1. Introduction

This project is a simple Python web application built using the Flask framework. It contains two routes that return messages in the browser. The application can be run locally and can also be used in a deployment workflow involving Jenkins and a webhook.

## 2. Architectural Diagram

```text
             User / Web Browser
                     |
               HTTP Request
                     |
                     v
              Flask Application
                  (app.py)
                 /        \
                /          \
          GET /              GET /hi
             |                  |
             v                  v
      Deployment message    HTML heading
             |                  |
             +--------+---------+
                      |
                      v
                HTTP Response
                      |
                      v
               User / Browser
```

**Note:** This diagram represents the application routes visible in `app(1).py`. Jenkins and webhook configuration are not included in the two supplied files.

## 3. Output

### Route `/`

When you open the home route, the application returns:

```text
successfully deployed python application through jenkins!!!!!!!!!, added webhook
```

### Route `/hi`

When you open `/hi`, the application returns an HTML heading:

```html
<h1>Hiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii from Flask & Docker</h1>
```

## 4. Input

The application accepts HTTP GET requests through these URLs:

- `http://127.0.0.1:5000/`
- `http://127.0.0.1:5000/hi`

No form fields or user-provided input parameters are defined in the supplied Python file. The application reads the `PORT` environment variable to select its listening port; if it is not set, the default is `5000`.

## 5. Background - PM2

PM2 is a process manager commonly used to keep applications running and manage restarts. The supplied files do not configure or use PM2. This Flask application includes Gunicorn in `requirements.txt`, which can be used as a WSGI server in a suitable deployment environment.

If PM2 is required for your deployment environment, its setup must be configured separately. It is not part of the current Python code.

## 6. Conclusion

This project demonstrates a basic Flask application with two routes. The `/` route displays a deployment-related message, while `/hi` displays an HTML heading referring to Flask and Docker. The dependencies are listed in `requirements.txt`. The provided files do not include a Jenkinsfile, webhook setup, or PM2 configuration, so those parts must be added separately if they are required for the full deployment workflow.
