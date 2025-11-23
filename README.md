# Color My Picture 🎨

A modern, AI-powered web application that allows users to upload images and colorize them using an interactive grid-based coloring system. Built with a futuristic UI design and a microservices architecture.

## ✨ Features

- **User Authentication**: Secure registration and login with JWT tokens
- **Image Upload**: Upload images in various formats (JPG, PNG, GIF, WEBP)
- **Interactive Coloring**: Grid-based coloring system with customizable grid sizes (2x2 to 8x8)
- **Color Selection**: Choose from AI-generated color palettes
- **Real-time Progress**: Track completion as you color each cell
- **Success Animation**: Celebratory animation when all cells are filled
- **Download Results**: Export your colored masterpiece as PNG
- **Gallery**: Browse and manage your uploaded images
- **Futuristic UI**: Modern design with neon accents, glass morphism, and smooth animations

## 🏗️ Architecture

This project follows a microservices architecture with the following components:

### Frontend
- **React 18** with TypeScript
- **Vite** for fast development and building
- **Tailwind CSS** for styling with custom futuristic theme
- **Radix UI** for accessible components
- **React Router** for navigation
- **React Hook Form** for form management
- **Axios** for API communication

### Backend Services

#### TypeScript Backend (NestJS)
- **NestJS** framework
- **PostgreSQL** database with TypeORM
- **JWT** authentication
- **Passport** strategies (Local, JWT, Refresh Token)
- **Swagger/OpenAPI** documentation
- RESTful API endpoints

#### Python Backend (FastAPI)
- **FastAPI** for high-performance API
- **PIL/Pillow** for image processing
- **K-means clustering** for color extraction
- Image analysis and colorization algorithms

### Infrastructure
- **Docker** and **Docker Compose** for containerization
- **PostgreSQL** database
- **Nginx** for frontend serving

## 📋 Prerequisites

- **Docker** and **Docker Compose** installed
- At least **2GB** of free disk space
- **Node.js 18+** (for local development)
- **Python 3.9+** (for local development)

## 🚀 Quick Start

### Using Docker (Recommended)

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd color-my-picture
   ```

2. **Create a `.env` file** (optional, defaults are provided):
   ```env
   DB_USERNAME=postgres
   DB_PASSWORD=postgres
   DB_DATABASE=colormypicture
   DB_PORT=5432
   JWT_KEY=your-secret-jwt-key-change-in-production
   ```

3. **Build and start all services**:
   ```bash
   docker-compose up -d --build
   ```

4. **Access the application**:
   - Frontend: http://localhost:3000
   - TypeScript Backend API: http://localhost:8080
   - Python Backend API: http://localhost:8081
   - Swagger Documentation: http://localhost:8080/api

5. **View logs**:
   ```bash
   docker-compose logs -f
   ```

6. **Stop all services**:
   ```bash
   docker-compose down
   ```

For more detailed Docker setup instructions, see [DOCKER_SETUP.md](./DOCKER_SETUP.md).

### Local Development

#### Frontend

```bash
cd color-my-picture-front
npm install
npm run dev
```

Frontend will be available at http://localhost:8080

#### TypeScript Backend

```bash
cd color-my-picture-back-ts
npm install
npm run start:dev
```

Backend will be available at http://localhost:8080

#### Python Backend

```bash
cd color-my-picture-back-python
pip install -r requirements.txt
uvicorn main:app --reload --port 8081
```

Python backend will be available at http://localhost:8081

## 📖 Usage

### Getting Started

1. **Register an account**:
   - Navigate to the registration page
   - Create an account with username, email, and password
   - Password requirements:
     - At least 8 characters
     - One uppercase letter
     - One lowercase letter
     - One number
     - One special character (!@_#$%^&*)

2. **Upload an image**:
   - Click on "Upload" in the navigation
   - Select an image file
   - Wait for upload confirmation

3. **Color your image**:
   - Go to "Gallery" and select an image
   - Choose grid size (2x2 to 8x8)
   - Select number of colors (2 to grid_size²/2)
   - Click on color palette items to select a color
   - Click on grid cells with matching numbers to color them
   - Drag to color multiple cells at once

4. **Download your result**:
   - When all cells are filled, a success animation appears
   - Click "Download Result" to save your colored image
   - Or use the download button in the completion banner

## 🗂️ Project Structure

```
color-my-picture/
├── color-my-picture-front/          # React frontend
│   ├── src/
│   │   ├── components/              # React components
│   │   ├── pages/                   # Page components
│   │   ├── _services/                # API services
│   │   ├── _types/                  # TypeScript types
│   │   ├── assets/                  # Styles and assets
│   │   └── lib/                     # Utility functions
│   ├── Dockerfile
│   └── package.json
│
├── color-my-picture-back-ts/        # NestJS backend
│   ├── src/
│   │   ├── auth/                    # Authentication module
│   │   ├── users/                    # User management
│   │   ├── images/                   # Image management
│   │   ├── http-request/             # Python backend proxy
│   │   └── database/                 # Database configuration
│   ├── Dockerfile
│   └── package.json
│
├── color-my-picture-back-python/    # FastAPI backend
│   ├── coloring/                    # Image processing modules
│   │   ├── color.py                 # Color extraction
│   │   ├── rendered.py              # Image rendering
│   │   └── treatment.py            # Image treatment
│   ├── main.py                      # FastAPI application
│   ├── Dockerfile
│   └── requirements.txt
│
├── docker-compose.yml               # Docker orchestration
├── DOCKER_SETUP.md                  # Docker setup guide
├── OPENAPI_SETUP.md                 # API documentation guide
└── README.md                        # This file
```

## 🔌 API Documentation

### Authentication Endpoints

- `POST /auth/register` - Register a new user
- `POST /auth/login` - Login and get access token

### Image Endpoints

- `POST /images/upload` - Upload an image
- `GET /images/download/:filename` - Download an image
- `GET /users/images` - Get user's images

### HTTP Request Endpoints (Python Backend Proxy)

- `POST /http-request/upload-image` - Upload image to Python backend
- `POST /http-request/data` - Get image analysis data

For complete API documentation, visit http://localhost:8080/api when the backend is running.

## 🛠️ Development

### Frontend Development

```bash
cd color-my-picture-front
npm install
npm run dev          # Start development server
npm run build        # Build for production
npm run lint         # Run linter
```

### Backend Development

```bash
cd color-my-picture-back-ts
npm install
npm run start:dev    # Start with hot reload
npm run build        # Build for production
npm run test         # Run tests
```

### Code Style

- Frontend: ESLint with TypeScript rules
- Backend: ESLint + Prettier
- Follow existing code patterns and conventions

## 🎨 UI Design

The application features a futuristic design system with:

- **Dark Theme**: Deep space-inspired backgrounds
- **Neon Colors**: Cyan, purple, pink, and green accents
- **Glass Morphism**: Frosted glass effects with backdrop blur
- **Smooth Animations**: Slide-up, fade-in, scale-in effects
- **Responsive Design**: Works on desktop, tablet, and mobile
- **Accessibility**: Radix UI components for screen reader support

## 🔒 Security

- JWT-based authentication with refresh tokens
- Password hashing with bcrypt
- CORS configuration
- Input validation on both frontend and backend
- SQL injection protection with TypeORM
- Secure cookie handling

## 📝 Environment Variables

### TypeScript Backend

```env
DB_HOST=postgres
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=postgres
DB_DATABASE=colormypicture
JWT_KEY=your-secret-jwt-key
API_URL=http://python-backend:8081
NODE_ENV=production
PORT=8080
```

### Frontend

The frontend currently uses hardcoded backend URLs. For production, configure environment variables in `vite.config.ts`.

## 🐛 Troubleshooting

### Common Issues

1. **Port conflicts**: Change ports in `docker-compose.yml`
2. **Database connection errors**: Ensure PostgreSQL is healthy before starting backend
3. **Build failures**: Clean build cache with `docker-compose build --no-cache`
4. **CORS errors**: Check backend CORS configuration

### View Logs

```bash
# All services
docker-compose logs -f

# Specific service
docker-compose logs -f typescript-backend
docker-compose logs -f python-backend
docker-compose logs -f frontend
```

## 🚢 Production Deployment

1. **Update environment variables** with production values
2. **Change default passwords** and JWT keys
3. **Enable HTTPS** with reverse proxy (Nginx, Traefik)
4. **Set up database backups**
5. **Configure resource limits** in docker-compose.yml
6. **Use secrets management** (Docker secrets, AWS Secrets Manager)
7. **Set up monitoring** and logging
8. **Update frontend** to use environment variables for API URLs

## 📄 License

This project is private and unlicensed.

## 🤝 Contributing

This is a private project. For contributions, please contact the project maintainers.

## 📧 Support

For issues and questions, please open an issue in the repository or contact the development team.

---

**Built with ❤️ using React, NestJS, FastAPI, and Docker**
