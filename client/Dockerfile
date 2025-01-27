# FROM node:16-alpine as builder
# WORKDIR '/app'
# COPY ./package.json ./
# RUN npm install
# COPY . .
# RUN npm run build

# FROM nginx
# EXPOSE 3000
# COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# COPY --from=builder /app/build /usr/share/nginx/html

# Stage 1: Build the application
FROM node:16-alpine AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy only the package.json and package-lock.json for dependency installation
COPY package.json package-lock.json ./

# Install dependencies
RUN npm ci --only=production

# Copy the rest of the application code
COPY . .

# Build the application for production
RUN npm run build

# Stage 2: Serve the application using Nginx
FROM nginx:stable-alpine

# Expose the port Nginx will use to serve the application
EXPOSE 3000

# Copy the custom Nginx configuration
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# Copy the built application from the builder stage to the Nginx HTML directory
COPY --from=builder /app/build /usr/share/nginx/html

# Add a health check for the container
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:3000 || exit 1
