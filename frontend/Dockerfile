# Stage 1: Build the frontend
FROM node:22 AS frontend-builder

WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install --upgradable npm

# Copy the rest of the frontend code
COPY . .

# Build the static files
RUN npm run build

# Stage 2: Serve using nginx
FROM nginx:alpine

# Copy build output to nginx public directory
COPY --from=frontend-builder /app/dist /app/node_modules /usr/share/nginx/html

# Copy custom nginx config 
COPY default.conf /etc/nginx/conf.d

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

