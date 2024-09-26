# Checkliste inde du deployer din Flask app. 

## Cors

Husk at give browsere tilladelse til at tilgå dine endpoints.

```
from flask_cors import CORS
CORS(app)
```

## Serverens ip adresse

i din app.run metode skal du skrive:

```
app.run(HOST=0.0.0.0)


)
