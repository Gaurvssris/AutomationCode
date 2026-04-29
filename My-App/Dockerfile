# # Stage 1: Builder
# FROM alpine AS builder
# WORKDIR /app

# # Copy index.html from local system
# COPY index.html .

# # Stage 2: NGINX
# FROM nginx:latest

# # Copy only required file
# COPY --from=builder /app/index.html /usr/share/nginx/html/index.html

# Stage 1: Build (Node)
# FROM node:18 AS builder

# WORKDIR /app

# COPY package.json .
# RUN npm install

# COPY . .
# RUN npm run build


# # Stage 2: Production (NGINX)
# FROM nginx:alpine

# COPY --from=builder /app/build /usr/share/nginx/html
# Stage 1: Build Stage (Node)
FROM node:18 AS builder

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .
RUN npm run build


# Stage 2: Production Stage (NGINX)
FROM nginx:alpine

COPY --from=builder /app/build /usr/share/nginx/html