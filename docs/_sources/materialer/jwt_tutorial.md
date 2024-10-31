# Implementing JWT Authentication with Cookies in a Dockerized Flask Microservice Architecture

In this tutorial, we'll build a Flask microservices application that uses JSON Web Tokens (JWT) for authentication, with the token stored in a cookie. The application will consist of two microservices and an API gateway where the authentication takes place. Additionally, we'll containerize each service using Docker.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Setting Up the Environment](#setting-up-the-environment)
- [Creating the API Gateway](#creating-the-api-gateway)
  - [Implementing JWT Authentication with Cookies](#implementing-jwt-authentication-with-cookies)
- [Creating Microservice 1](#creating-microservice-1)
- [Creating Microservice 2](#creating-microservice-2)
- [Dockerizing the Services](#dockerizing-the-services)
  - [Creating Dockerfiles](#creating-dockerfiles)
  - [Creating a `docker-compose.yml` File](#creating-a-docker-composeyml-file)
- [Running the Services with Docker Compose](#running-the-services-with-docker-compose)
- [Testing the Application](#testing-the-application)
  - [Using Postman to Test the API](#using-postman-to-test-the-api)
    - [1. Log In and Obtain JWT Token Cookie](#1-log-in-and-obtain-jwt-token-cookie)
    - [2. Access Microservice 1](#2-access-microservice-1)
    - [3. Access Microservice 2](#3-access-microservice-2)
    - [4. Access Without Token](#4-access-without-token)
    - [5. Log Out](#5-log-out)
- [Conclusion](#conclusion)

## Prerequisites

- Docker and Docker Compose installed on your machine
- Python 3.7 or higher (for development)
- Basic knowledge of Flask, RESTful APIs, and Docker
- Familiarity with JWT concepts
- [Postman](https://www.postman.com/downloads/) installed for API testing

## Project Structure

```
jwt_microservices/
├── api_gateway/
│   ├── gateway.py
│   └── Dockerfile
├── microservice1/
│   ├── service1.py
│   └── Dockerfile
├── microservice2/
│   ├── service2.py
│   └── Dockerfile
├── docker-compose.yml
└── requirements.txt
```

## Setting Up the Environment

First, create a project directory and navigate into it:

```bash
mkdir jwt_microservices
cd jwt_microservices
```

Create a `requirements.txt` file with the following contents:

```txt
Flask==2.2.2
PyJWT==2.4.0
requests==2.28.1
```

## Creating the API Gateway

Create a directory for the API gateway:

```bash
mkdir api_gateway
```

Create a file named `gateway.py` inside the `api_gateway` directory.

```python
# api_gateway/gateway.py
from flask import Flask, request, jsonify, make_response
import jwt
import requests
from datetime import datetime, timedelta
import os

app = Flask(__name__)
app.config['SECRET_KEY'] = os.environ.get('SECRET_KEY', 'your_secret_key')

# In-memory user store for demonstration purposes
users = {
    'user1': 'password1',
    'user2': 'password2'
}

@app.route('/login', methods=['POST'])
def login():
    auth_data = request.json
    username = auth_data.get('username')
    password = auth_data.get('password')

    if not username or not password or users.get(username) != password:
        return jsonify({'message': 'Invalid credentials'}), 401

    token = jwt.encode({
        'sub': username,
        'iat': datetime.utcnow(),
        'exp': datetime.utcnow() + timedelta(minutes=30)
    }, app.config['SECRET_KEY'], algorithm='HS256')

    response = make_response(jsonify({'message': 'Logged in successfully'}))
    response.set_cookie('token', token, httponly=True, samesite='Strict')
    return response

@app.route('/logout', methods=['POST'])
def logout():
    response = make_response(jsonify({'message': 'Logged out successfully'}))
    response.set_cookie('token', '', expires=0)
    return response

def verify_token():
    token = request.cookies.get('token')
    if not token:
        return None
    try:
        payload = jwt.decode(token, app.config['SECRET_KEY'], algorithms=['HS256'])
        return payload
    except jwt.ExpiredSignatureError:
        return 'expired'
    except jwt.InvalidTokenError:
        return None

@app.route('/service1', methods=['GET', 'POST'])
def service1():
    payload = verify_token()
    if payload == 'expired':
        return jsonify({'message': 'Token expired'}), 401
    if payload is None:
        return jsonify({'message': 'Invalid token'}), 401

    # Forward the request to microservice1
    resp = requests.request(
        method=request.method,
        url='http://microservice1:5001' + request.path,
        headers={key: value for (key, value) in request.headers if key != 'Host'},
        data=request.get_data(),
        cookies=request.cookies,
        allow_redirects=False)
    return (resp.content, resp.status_code, resp.headers.items())

@app.route('/service2', methods=['GET', 'POST'])
def service2():
    payload = verify_token()
    if payload == 'expired':
        return jsonify({'message': 'Token expired'}), 401
    if payload is None:
        return jsonify({'message': 'Invalid token'}), 401

    # Forward the request to microservice2
    resp = requests.request(
        method=request.method,
        url='http://microservice2:5002' + request.path,
        headers={key: value for (key, value) in request.headers if key != 'Host'},
        data=request.get_data(),
        cookies=request.cookies,
        allow_redirects=False)
    return (resp.content, resp.status_code, resp.headers.items())

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000, debug=True)
```

### Implementing JWT Authentication with Cookies

In the API gateway, we're handling JWT authentication by storing the token in a cookie:

1. **Set the Token Cookie**: Upon successful login, the JWT token is stored in an HTTP-only cookie.
2. **Verify the Token**: A helper function `verify_token()` extracts and verifies the token from the cookie.
3. **Handle Exceptions**: Manage cases where the token is expired or invalid.
4. **Forward the Request**: If the token is valid, forward the request to the appropriate microservice.

## Creating Microservice 1

Create a directory for microservice1:

```bash
mkdir microservice1
```

Create a file named `service1.py` inside the `microservice1` directory.

```python
# microservice1/service1.py
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/service1', methods=['GET', 'POST'])
def handle_service1():
    return jsonify({'message': 'Response from Microservice 1'})

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5001, debug=True)
```

## Creating Microservice 2

Create a directory for microservice2:

```bash
mkdir microservice2
```

Create a file named `service2.py` inside the `microservice2` directory.

```python
# microservice2/service2.py
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/service2', methods=['GET', 'POST'])
def handle_service2():
    return jsonify({'message': 'Response from Microservice 2'})

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5002, debug=True)
```

## Dockerizing the Services

### Creating Dockerfiles

Create a `Dockerfile` for each service.

#### API Gateway Dockerfile

Create `api_gateway/Dockerfile`:

```dockerfile
# api_gateway/Dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY gateway.py .

ENV SECRET_KEY your_secret_key

EXPOSE 5000

CMD ["python", "gateway.py"]
```

#### Microservice 1 Dockerfile

Create `microservice1/Dockerfile`:

```dockerfile
# microservice1/Dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY service1.py .

EXPOSE 5001

CMD ["python", "service1.py"]
```

#### Microservice 2 Dockerfile

Create `microservice2/Dockerfile`:

```dockerfile
# microservice2/Dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY service2.py .

EXPOSE 5002

CMD ["python", "service2.py"]
```

### Creating a `docker-compose.yml` File

In the root of your project directory, create a `docker-compose.yml` file:

```yaml
# docker-compose.yml
version: '3.8'

services:
  api_gateway:
    build: ./api_gateway
    ports:
      - "5000:5000"
    depends_on:
      - microservice1
      - microservice2

  microservice1:
    build: ./microservice1
    ports:
      - "5001:5001"

  microservice2:
    build: ./microservice2
    ports:
      - "5002:5002"
```

## Running the Services with Docker Compose

From the root of your project directory, run:

```bash
docker-compose up --build
```

This command will build the Docker images and start all the services defined in `docker-compose.yml`.

## Testing the Application

### Using Postman to Test the API

We'll use Postman to interact with our API and test the authentication flow.

#### 1. Log In and Obtain JWT Token Cookie

- **Open Postman**.
- **Create a new POST request** to `http://localhost:5000/login`.
- **Set Headers**:
  - Click on the "Headers" tab.
  - Ensure that `Content-Type` is set to `application/json`.
- **Set Body**:
  - Click on the "Body" tab.
  - Select `raw` and choose `JSON` from the dropdown.
  - Enter the following JSON data:

    ```json
    {
      "username": "user1",
      "password": "password1"
    }
    ```

- **Send the Request**:
  - Click the "Send" button.
- **Check the Response**:
  - You should receive a response with a message indicating a successful login:

    ```json
    {
      "message": "Logged in successfully"
    }
    ```

- **Manage Cookies**:
  - Click on the "Cookies" link (below the "Send" button).
  - Ensure that a cookie named `token` is stored for `localhost`.
  - Postman automatically saves cookies from responses, so you should see the `token` cookie listed.

#### 2. Access Microservice 1

- **Create a new GET request** to `http://localhost:5000/service1`.
- **Ensure Cookies are Sent**:
  - Postman automatically includes saved cookies when making requests to the same host.
  - Verify that the `token` cookie is present by clicking on the "Cookies" link.
- **Send the Request**:
  - Click the "Send" button.
- **Check the Response**:
  - You should receive a response from Microservice 1:

    ```json
    {
      "message": "Response from Microservice 1"
    }
    ```

#### 3. Access Microservice 2

- **Create a new GET request** to `http://localhost:5000/service2`.
- **Ensure Cookies are Sent**:
  - As before, make sure the `token` cookie is present.
- **Send the Request**:
  - Click the "Send" button.
- **Check the Response**:
  - You should receive a response from Microservice 2:

    ```json
    {
      "message": "Response from Microservice 2"
    }
    ```

#### 4. Access Without Token

To test access without the token:

- **Delete the `token` Cookie**:
  - Click on the "Cookies" link.
  - Select `localhost`.
  - Hover over the `token` cookie and click the "X" to delete it.
- **Create a new GET request** to `http://localhost:5000/service1`.
- **Send the Request**:
  - Click the "Send" button.
- **Check the Response**:
  - You should receive an error message indicating an invalid token:

    ```json
    {
      "message": "Invalid token"
    }
    ```

#### 5. Log Out

- **Re-Login if Necessary**:
  - If you deleted the `token` cookie in the previous step, log in again to obtain a new token cookie.
- **Create a new POST request** to `http://localhost:5000/logout`.
- **Ensure Cookies are Sent**:
  - Verify that the `token` cookie is present.
- **Send the Request**:
  - Click the "Send" button.
- **Check the Response**:
  - You should receive a message indicating a successful logout:

    ```json
    {
      "message": "Logged out successfully"
    }
    ```

- **Verify Token Cookie is Cleared**:
  - Click on the "Cookies" link.
  - The `token` cookie should no longer be present under `localhost`.

- **Attempt to Access a Service After Logout**:
  - **Create a new GET request** to `http://localhost:5000/service1`.
  - **Send the Request**.
  - **Check the Response**:
    - You should receive an error message indicating an invalid token:

      ```json
      {
        "message": "Invalid token"
      }
      ```

## Conclusion

We've successfully built a Flask microservices application with JWT authentication using cookies and containerized each service using Docker. We've also demonstrated how to test the application using Postman, a powerful API development tool.

### Key Takeaways

- **JWT in Cookies**: Storing the JWT in a cookie enhances security by utilizing HTTP-only cookies, which are not accessible via JavaScript.
- **Containerization**: Dockerizing each service ensures consistent environments and simplifies deployment.
- **Microservices Interaction**: Each microservice remains independent, promoting modularity and ease of maintenance.
- **Using Postman**: Postman simplifies API testing by managing cookies, headers, and request bodies effectively.

### Next Steps

- **Secure Cookies**: In a production environment, ensure cookies are marked as `Secure` and consider using HTTPS.
- **Environment Variables**: Manage secrets and configuration using environment variables or a secrets manager.
- **Scaling Services**: Use orchestration tools like Kubernetes for scaling and managing your services.
- **Database Integration**: Extend the application by integrating databases for persistent storage.