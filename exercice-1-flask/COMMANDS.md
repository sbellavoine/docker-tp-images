# Je construis l'image Docker
docker build -t hello-flask:1.0.0 .

# Je lance le conteneur
docker run -p 5000:5000 hello-flask:1.0.0

# Je cree le tag latest
docker tag hello-flask:1.0.0 hello-flask:latest

# Je verifie les images locales
docker images