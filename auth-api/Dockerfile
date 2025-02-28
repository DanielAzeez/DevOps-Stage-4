# Use Go 1.21.1 as the base image
FROM golang:1.21.1-alpine AS builder

# Set working directory
WORKDIR /app

# Copy the Go module files
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy all source files into the container
COPY . .

# Build the application
RUN go build -o auth-api .

# Use a smaller base image for the final runtime
FROM alpine:latest

# Set working directory
WORKDIR /app

# Copy the built binary from the builder stage
COPY --from=builder /app/auth-api .

# Expose the required port
EXPOSE 8081

# Start the auth-api application
CMD ["./auth-api"]