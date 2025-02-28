# Use a stable Node.js version
FROM node:12-alpine

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install build tools
RUN apk add --no-cache python3 make g++

# Clear npm cache and install dependencies
RUN npm cache clean --force && npm install

# Copy the rest of the application code
COPY . .

# Build the frontend
RUN npm run build

# Expose the frontend port
EXPOSE 8080

# Start the frontend application
CMD ["npm", "start"]