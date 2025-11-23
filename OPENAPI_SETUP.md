# OpenAPI/Swagger Documentation

Both backend services now have OpenAPI/Swagger documentation enabled.

## TypeScript Backend (NestJS)

### Access
- **Swagger UI**: `http://localhost:8080/api`
- **JSON Schema**: `http://localhost:8080/api-json`

### Features
- Interactive API documentation
- JWT Bearer token authentication support
- Cookie-based authentication support
- Request/response examples
- All endpoints documented with descriptions

### Authentication
The Swagger UI supports two authentication methods:
1. **JWT Bearer Token**: Use the "Authorize" button and select "JWT-auth"
2. **Cookie Authentication**: Uses the `access_token` cookie

### Endpoints Documented
- `/auth/login` - User login
- `/auth/register` - User registration
- `/images/*` - Image management endpoints
- `/users/*` - User management endpoints
- `/friends/*` - Friends management endpoints

## Python Backend (FastAPI)

### Access
- **Swagger UI**: `http://localhost:8081/docs`
- **ReDoc**: `http://localhost:8081/redoc`
- **OpenAPI JSON**: `http://localhost:8081/openapi.json`

### Features
- Interactive API documentation (Swagger UI)
- Alternative documentation (ReDoc)
- Request/response validation
- Field validation with constraints
- Detailed endpoint descriptions

### Endpoints Documented
- `GET /` - Health check
- `POST /upload/` - Upload an image file
- `POST /data/` - Get image analysis data
- `POST /result/` - Generate colored image

### Request Body Example
```json
{
  "filename": "image.jpg",
  "nb_colors": 10,
  "nb_cases": 50
}
```

## Installation

### TypeScript Backend
The `@nestjs/swagger` package has been added to `package.json`. Install it with:
```bash
cd color-my-picture-back-ts
npm install
```

### Python Backend
FastAPI includes OpenAPI support by default. No additional installation needed.

## Usage

1. **Start the services**:
   ```bash
   docker-compose up -d
   ```

2. **Access the documentation**:
   - NestJS: http://localhost:8080/api
   - FastAPI: http://localhost:8081/docs

3. **Test endpoints** directly from the Swagger UI

## Notes

- The Swagger UI allows you to test API endpoints directly
- Authentication tokens can be set in the Swagger UI for protected endpoints
- All endpoints include request/response examples
- Field validations are documented (e.g., `nb_colors` must be between 1-256)

