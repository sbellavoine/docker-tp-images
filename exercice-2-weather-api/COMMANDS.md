# Je me place dans le dossier du projet
cd exercice-2-weather-api

# Je construis l'image Docker
docker build -t sbellavoine/weather-api:1.0.0 .

# Je lance le conteneur
docker run -p 3005:3000 sbellavoine/weather-api:1.0.0

# Je teste l'API dans le navigateur
# http://localhost:3005/health
# http://localhost:3005/api/weather/paris

# Je me connecte a Docker Hub
docker login

# Je publie l'image avec le tag 1.0.0
docker push sbellavoine/weather-api:1.0.0

# Je cree le tag latest
docker tag sbellavoine/weather-api:1.0.0 sbellavoine/weather-api:latest

# Je publie le tag latest
docker push sbellavoine/weather-api:latest

# Je verifie les images locales
docker images