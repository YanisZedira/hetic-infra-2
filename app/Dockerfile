<<<<<<< HEAD
# Utiliser une image Node.js de base avec une version alpine pour un poids réduit
FROM node:16.20.1-alpine3.17

# Ajouter un label pour le mainteneur
LABEL maintainer="myanis.zedira@gmail.com"

# Spécifier l'environnement de déploiement
ENV NODE_ENV=production

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Copier le fichier package.json et package-lock.json pour installer les dépendances
COPY app/package*.json ./
RUN npm install

# Copier le reste des fichiers de l'application
COPY app /app

# Créer un utilisateur non-root pour exécuter l'application en sécurité
RUN adduser -D appuser && chown -R appuser /app
USER appuser

# Exposer le port 3000 pour l'application
EXPOSE 3000

# Démarrer l'application
CMD ["node", "app.js"]
=======
# Utiliser une image Node.js de base avec une version alpine pour un poids réduit
FROM node:16.20.1-alpine3.17

# Ajouter un label pour le mainteneur
LABEL maintainer="myanis.zedira@gmail.com"

# Spécifier l'environnement de déploiement
ENV NODE_ENV=production

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Copier le fichier package.json et package-lock.json pour installer les dépendances
COPY app/package*.json ./
RUN npm install

# Copier le reste des fichiers de l'application
COPY app /app

# Créer un utilisateur non-root pour exécuter l'application en sécurité
RUN adduser -D appuser && chown -R appuser /app
USER appuser

# Exposer le port 3000 pour l'application
EXPOSE 3000

# Démarrer l'application
CMD ["node", "app.js"]
>>>>>>> 3ab9f0e939acafbb66463c9e9fd587c561b3298a
