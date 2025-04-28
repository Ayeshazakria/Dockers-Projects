FROM node:18-alpine AS installer
WORKDIR /app
COPY package*.json ./
# Disable SSL verification
RUN npm config set strict-ssl false
RUN npm install
COPY . .
RUN npm run build

FROM nginx:latest AS deployer
COPY --from=installer /app/build  /usr/share/nginx/html

