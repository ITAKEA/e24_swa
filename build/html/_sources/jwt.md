# Authorization med JWT

## Læringsmål
* Kunne forklare begrebet Authendication i forbindelse med en Microservice arkitektur
* Kunne forklare begrebet Authorisation i forbindelse med en Microservice arkitektur




## Forberedelse

## Dagens indhold


## Hjemmesrabejde


## Materialer
* [JWT Authentication Explained](https://www.youtube.com/watch?v=iHNkGQyJxJs)
* [JWT Debugger](https://jwt.io/#debugger-io)

* [What is JWT? JSON Web Tokens Explained (Java Brains)](https://www.youtube.com/watch?v=soGRyl9ztjI)
* [What is the structure of a JWT - Java Brains](https://www.youtube.com/watch?v=_XbXkVdoG_0)

### Øvelser

#### Øvelse med app.py og auth.py services i samarbejde

1. Kig på følgende to python filer iKør dem og forstå hvad der foregår i koden linie for linie. 

```
# auth.py

from flask import Flask, request, jsonify
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
            'user': username
        }, app.config['SECRET_KEY'], algorithm='HS256')
        
        return jsonify({"token": token})
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

def token_required(f):
    def wrapped(*args, **kwargs):
        token = request.headers.get('Authorization')
        if not token:
            return jsonify({"message": "Token is missing!"}), 403

        try:
            jwt.decode(token, app.config['SECRET_KEY'], algorithms=['HS256'])
        except jwt.ExpiredSignatureError:
            return jsonify({"message": "Token is expired!"}), 403
        except jwt.InvalidTokenError:
            return jsonify({"message": "Invalid token!"}), 403

        return f(*args, **kwargs)
    return wrapped

@app.route("/")
@token_required
def home():
    return "Hello, this is a Flask Microservice"

if __name__ == "__main__":
    app.run(debug=True, host="0.0.0.0", port=5000)
```
