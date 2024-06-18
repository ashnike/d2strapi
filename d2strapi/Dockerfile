# Stage 1: Build Stage
FROM node:20-alpine AS builder

WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application source code
COPY . .

# Stage 2: Runtime Stage
FROM node:20-alpine

WORKDIR /usr/src/app

# Copy only the necessary files from the builder stage
COPY --from=builder /usr/src/app .

# Expose the Strapi port
EXPOSE 1337

# Start Strapi
CMD ["npm", "run", "develop"]
