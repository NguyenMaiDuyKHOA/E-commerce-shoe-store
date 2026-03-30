FROM node:22.11.0

WORKDIR /app

# Install build dependencies
RUN apt-get update && apt-get install -y \
    python3 \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

COPY package*.json ./
RUN npm ci

# Remove any cached node_modules and rebuild bcrypt for Linux
RUN rm -rf node_modules && npm ci && npm rebuild

COPY . .

EXPOSE 4000
CMD ["npm", "start"]