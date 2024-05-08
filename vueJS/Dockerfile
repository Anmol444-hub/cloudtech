# Use the official lightweight Node.js 14 image
FROM node:16-alpine as build-stage

# Set working directory
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the application
COPY . .

# Build the Vue.js app for production
RUN npm run build

# Use NGINX to serve the built files
FROM nginx:alpine
COPY --from=build-stage /app/dist /usr/share/nginx/html
