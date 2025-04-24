FROM node:18-alpine

WORKDIR /app

# Install required build tools for sqlite3 and CA support
RUN apk add --no-cache python3 make g++ ca-certificates

# Disable SSL verification globally (for dev/testing only)
ENV NODE_TLS_REJECT_UNAUTHORIZED=0
RUN yarn config set strict-ssl false

# Copy dependencies and install
COPY package.json yarn.lock ./
RUN yarn install --production

# Copy source code
COPY . .

EXPOSE 3000
CMD ["node", "src/index.js"]

