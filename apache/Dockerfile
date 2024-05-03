# Use Alpine Linux as base image
FROM alpine:latest AS builder

# Install dependencies (example: git, build tools)
RUN apk add --no-cache git gcc g++ musl-dev go

# Set working directory
WORKDIR /app

# git the project
RUN git clone https://github.com/skandix/Beetroot.git

WORKDIR /app/Beetroot
# Build your application 
RUN go mod download github.com/PuerkitoBio/purell
RUN go get github.com/betauia/beetroot/api
RUN go get github.com/betauia/beetroot/config
RUN go build -o beetroot cmd/beetroot/main.go

# Use a smaller base image for the runtime environment
FROM alpine:latest

# Set timezone (example: UTC)
ENV TZ=UTC

# Set working directory
WORKDIR /app

# Copy compiled binary from builder stage
COPY --from=builder /app/Beetroot/beetroot .

# Expose port 8080
EXPOSE 8080

# Command to run the application
CMD ["./beetroot"]
CMD ["echo hello"]
