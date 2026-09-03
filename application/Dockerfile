# Stage 1: Build the application
FROM node:20-alpine AS builder

WORKDIR /app

# Copy dependency files
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy application source code
COPY . .

# TMDB API key passed during Docker build
ARG VITE_APP_TMDB_V3_API_KEY
ENV VITE_APP_TMDB_V3_API_KEY=$VITE_APP_TMDB_V3_API_KEY

# Build the Vite application
RUN npm run build


# Stage 2: Serve with Nginx
FROM nginx:alpine

# Copy built files
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
