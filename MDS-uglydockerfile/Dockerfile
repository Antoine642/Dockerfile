# Image de base Node.js
FROM node:14-alpine

# Installation des dépendances
WORKDIR /app
COPY package.json .
RUN npm install

# Ajout des fichiers du projet
COPY . .

# Build de l'application Vue.js
RUN npm run build

# Utilisation d'une image légère pour Nginx
FROM nginx:alpine

# Copie des fichiers de build vers le dossier de Nginx
COPY --from=0 /app/dist /usr/share/nginx/html

EXPOSE 80
# Démarrage de Nginx
CMD ["nginx", "-g", "daemon off;"]
