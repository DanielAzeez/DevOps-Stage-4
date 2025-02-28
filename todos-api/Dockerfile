# Use Node.js as the base image
FROM node:20-alpine

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the required port
EXPOSE 8082

# Start the todos API
CMD ["node", "server.js"]