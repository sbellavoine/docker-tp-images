# Je me place dans le dossier de l'exercice
cd exercice-3-stats-api

# Je construis l'image Docker de la version 1.0.0
docker build -t sbellavoine/stats-api:1.0.0 .

# Je lance le conteneur de la version 1.0.0
docker run -p 8085:8080 sbellavoine/stats-api:1.0.0

# Je teste l'endpoint /api/stats
Invoke-RestMethod -Uri http://localhost:8085/api/stats -Method Post -ContentType "application/json" -Body '{"numbers":[1,2,3,4,5]}'

# Je publie l'image 1.0.0 sur Docker Hub
docker push sbellavoine/stats-api:1.0.0

# Je modifie l'application pour créer la version 2.0.0
# - j'ajoute l'endpoint /api/stats/median dans app.py
# - je mets à jour requirements.txt
# - je mets en place un Dockerfile avec un multistage build

# Je construis l'image Docker de la version 2.0.0
docker build -t sbellavoine/stats-api:2.0.0 .

# Je lance le conteneur de la version 2.0.0
docker run -p 8086:8080 sbellavoine/stats-api:2.0.0

# Je teste l'endpoint /api/stats
Invoke-RestMethod -Uri http://localhost:8086/api/stats -Method Post -ContentType "application/json" -Body '{"numbers":[1,2,3,4,5]}'

# Je teste l'endpoint /api/stats/median
Invoke-RestMethod -Uri http://localhost:8086/api/stats/median -Method Post -ContentType "application/json" -Body '{"numbers":[1,2,3,4,5]}'

# Je publie l'image 2.0.0 sur Docker Hub
docker push sbellavoine/stats-api:2.0.0

# Je crée le tag latest à partir de la version 2.0.0
docker tag sbellavoine/stats-api:2.0.0 sbellavoine/stats-api:latest

# Je publie le tag latest sur Docker Hub
docker push sbellavoine/stats-api:latest

# Je vérifie les images Docker présentes sur ma machine
docker images