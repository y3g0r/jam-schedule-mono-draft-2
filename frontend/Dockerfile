# Stage 1: Build the React app
FROM node:20-alpine AS builder
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: Serve with a minimal nginx instance
FROM nginxinc/nginx-unprivileged:alpine
# Use unprivileged nginx for lower resource usage and security
COPY --from=builder /app/dist /usr/share/nginx/html
COPY ./nginx.main.conf /etc/nginx/nginx.conf
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 8080
USER 1001
CMD ["nginx", "-g", "daemon off;"] 