# Go Project

![Go Build Status](https://github.com/yourusername/gogin/workflows/Go%20CI/badge.svg)
![Go Version](https://img.shields.io/badge/go%20version-1.21+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## Project Overview

A modern Go application built with best practices, featuring clean architecture and robust routing.

## Getting Started

### Prerequisites

- **Go 1.21 or higher**
- **Git** (for version control)

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/gogin.git
cd gogin

# Download dependencies
make dependencies
# or
 go mod download
```

### Running the Application

```bash
# Run the application in development mode
make run
# or
 go run main.go

# Build for production
make build
# or
 go build -o app .
```

## Project Structure

```
.
├── cmd/
│   └── main.go          # Application entry point
├── internal/
│   ├── handler/         # HTTP handlers
│   ├── service/         # Business logic services
│   └── repository/      # Data persistence
├── routes.go            # HTTP routing configuration
├── config/              # Application configuration
├── docs/                # Documentation
├── test/                # Test files
├── .env.example         # Environment variables template
└── Makefile            # Development and build commands
```

## Key Features

- **Clean Architecture**: Separation of concerns with dependency injection
- **RESTful API Design**: Consistent and well-documented endpoints
- **Error Handling**: Comprehensive error management and logging
- **Configuration Management**: Environment-based configuration
- **Testing**: Unit and integration test coverage
- **Docker Support**: Containerized deployment ready

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Health check endpoint |
| GET | `/api/resource` | List all resources |
| POST | `/api/resource` | Create a new resource |
| GET | `/api/resource/{id}` | Get resource by ID |
| PUT | `/api/resource/{id}` | Update resource by ID |
| DELETE | `/api/resource/{id}` | Delete resource by ID |

## Development Commands

| Command | Description |
|---------|-------------|
| `make dev` | Run application in development mode with auto-refresh |
| `make test` | Run all tests with coverage report |
| `make lint` | Run linter and formatter |
| `make migrate` | Apply database migrations |
| `make swagger` | Generate API documentation |

## Testing

Run the test suite to ensure everything works:

```bash
make test
# or
go test ./...
```

Test coverage is automatically generated and can be viewed using:

```bash
go tool cover -html=coverage.out
```

## Configuration

### Environment Variables

Create a `.env` file with the following variables:

```env
PORT=8080
DATABASE_URL=postgresql://user:password@localhost:5432/appdb
SECRET_KEY=your-secret-key-here
LOG_LEVEL=info
```

### Configuration Management

See `config/` directory for detailed configuration options and environment-specific settings.

## Docker

### Quick Start

```bash
# Build and run with Docker Compose
docker-compose up --build

# Run tests in container
docker-compose run app go test ./...
```

### Dockerfile

```dockerfile
FROM golang:1.21-alpine AS builder
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN go build -o app .

FROM alpine:latest
COPY --from=builder /app/app /app
EXPOSE 8080
CMD ["./app"]
```

## Contributing

We welcome contributions! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-name/awesome-feature
   ```
3. **Make your changes** and ensure all tests pass
4. **Write tests** for any new functionality
5. **Submit a pull request**

## Code Standards

- **Code Style**: Follow standard Go formatting (`gofmt`)
- **Linting**: Use `golangci-lint` for code analysis
- **Testing**: 80%+ test coverage required for new features
- **Documentation**: Document all public APIs

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact

For questions, issues, or suggestions:

- GitHub Issues
- Open an issue on the repository
- Star the project if you find it useful!

## Acknowledgements

Special thanks to:
- Go Community for incredible tooling
- Open source contributors
- All users who provide feedback and report issues