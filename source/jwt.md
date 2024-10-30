# Authorization med JWT
I dag skal vi arbejde med Arthendication og Arthorization med Json Web Token (JWT).

## Læringsmål
* Kunne forklare begrebet Authendication i forbindelse med en Microservice arkitektur
* Kunne forklare begrebet Authorisation i forbindelse med en Microservice arkitektur
* 

## Forberedelse
* [What is JWT? JSON Web Tokens Explained (Java Brains)](https://www.youtube.com/watch?v=soGRyl9ztjI)
* [What is the structure of a JWT - Java Brains](https://www.youtube.com/watch?v=_XbXkVdoG_0)

## Dagens indhold


## Hjemmesrabejde


## Materialer
* [JWT Authentication Explained](https://www.youtube.com/watch?v=iHNkGQyJxJs)
* [JWT Debugger](https://jwt.io/#debugger-io)

* [What is JWT? JSON Web Tokens Explained (Java Brains)](https://www.youtube.com/watch?v=soGRyl9ztjI)
* [What is the structure of a JWT - Java Brains](https://www.youtube.com/watch?v=_XbXkVdoG_0)

### Øvelser

#### Øvelse med app.py og auth.py services i samarbejde

1. Kig på følgende to python filer. Kør dem og forstå hvad der foregår i koden linie for linie. 

```
# auth.py

from flask import Flask, request, jsonify, make_response
import jwt
import datetime

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'

users = {
    'testuser': 'password123'
}

@app.route("/login", methods=["POST"])
def login():
    data = request.get_json()
    
    username = data.get('username')
    password = data.get('password')
    
    if not username or not password:
        return jsonify({"message": "Username and Password required"}), 400

    if users.get(username) and users.get(username) == password:
        token = jwt.encode({
            'user': username,
            'exp': datetime.datetime.utcnow() + datetime.timedelta(hours=1)
        }, app.config['SECRET_KEY'], algorithm='HS256')
        
        response = make_response(jsonify({"message": "Login successful"}), 200)
        response.headers['Authorization'] = f'Bearer {token}'
        return response
    else:
        return jsonify({"message": "Invalid Credentials"}), 401

if __name__ == "__main__":
    app.run(debug=True, host="0.0.0.0", port=5001)

```


```
# app.py

from flask import Flask, jsonify, request
import jwt

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'

def verify_token(token):
    if not token:
        return jsonify({"message": "Token is missing!"}), 403

    try:
        token = token.split(" ")[1] if token.startswith("Bearer ") else token
        jwt.decode(token, app.config['SECRET_KEY'], algorithms=['HS256'])
    except jwt.ExpiredSignatureError:
        return jsonify({"message": "Token is expired!"}), 403
    except jwt.InvalidTokenError:
        return jsonify({"message": "Invalid token!"}), 403

    return None

@app.route("/")
def home():
    token = request.headers.get('Authorization')
    token_error = verify_token(token)
    if token_error:
        return token_error
    return "Hello, this is a Flask Microservice"

if __name__ == "__main__":
    app.run(debug=True, host="0.0.0.0", port=5000)
```
