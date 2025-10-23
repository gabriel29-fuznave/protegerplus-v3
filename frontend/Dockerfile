# Stage 1: Build stage
FROM node:16-alpine as builder
WORKDIR /app
COPY package.json .
# Removida a linha 'COPY package-lock.json .' pois o arquivo não foi gerado
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Production stage
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
