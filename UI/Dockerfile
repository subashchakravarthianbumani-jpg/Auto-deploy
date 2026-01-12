# -------- BUILD STAGE --------
FROM node:20 AS build
WORKDIR /app

# Copy package files first (cache)
COPY UI/package*.json ./
RUN npm install

# Copy UI source
COPY UI/ .

# Build angular
RUN npm run build

# -------- RUNTIME STAGE --------
FROM nginx:alpine

# 🔥 IMPORTANT FIX (project folder name)
COPY --from=build /app/dist/ui-base /usr/share/nginx/html

EXPOSE 80
