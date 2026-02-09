# RDash - Complete Project Management System

A full-featured project management system built with Angular frontend and PHP backend, deployed on Render.

## 🚀 Live Demo
- **Frontend:** https://rdash-frontend.onrender.com
- **Backend API:** https://rdash-backend.onrender.com

## 📋 Features

### ✨ Core Features
- **User Authentication** with role-based access (Admin, Super Admin, Editor, User)
- **Project Management** with state/city dropdowns
- **Task Management** with comprehensive status tracking
- **Comment System** with media attachments (up to 5MB)
- **Real-time Dashboard** with statistics and analytics

### 🛠️ Technical Features
- **Angular 18** frontend with responsive design
- **PHP 8+** backend with RESTful API
- **SQLite database** with full CRUD operations
- **File Upload System** with size limits and validation
- **CORS Configuration** for cross-origin requests

## 🏗️ Architecture

```
├── src/                    # Angular Frontend
│   ├── app/
│   │   ├── components/     # Angular Components
│   │   ├── Services/       # HTTP Services
│   │   └── modules/        # Angular Modules
├── server/                 # PHP Backend
│   ├── route.php          # Main API Router
│   ├── uploads/           # File Uploads
│   └── dbo/data/          # SQLite Database
└── dist/                  # Built Angular App
```

## 🚀 Deployment on Render

### Prerequisites
- Render account (free tier available)
- GitHub repository with the code

### Step 1: Backend Deployment

1. **Create Web Service**
   - Go to Render Dashboard → New → Web Service
   - Connect your GitHub repository
   - **Name:** `rdash-backend`
   - **Runtime:** `PHP`
   - **Build Command:** `composer install --no-dev --optimize-autoloader`
   - **Start Command:** `php -S 0.0.0.0:$PORT server/route.php`

2. **Environment Variables**
   ```
   PORT=8000
   PHP_INI_DIR=/opt/render/project/src
   ```

### Step 2: Frontend Deployment

1. **Create Static Site**
   - Go to Render Dashboard → New → Static Site
   - Connect your GitHub repository
   - **Name:** `rdash-frontend`
   - **Build Command:** `npm install && npm run build --prod`
   - **Publish Directory:** `dist/rdash`

2. **Environment Variables**
   ```
   NG_BUILD_COMMAND=ng build --configuration production --base-href /
   ```

### Step 3: Configuration Updates

1. **Update Frontend API URL**
   ```typescript
   // src/app/Services/http-client.service.ts
   private baseUrl = 'https://rdash-backend.onrender.com';
   ```

2. **Update Backend CORS**
   ```php
   // server/route.php
   header("Access-Control-Allow-Origin: https://rdash-frontend.onrender.com");
   ```

## 🛠️ Local Development

### Prerequisites
- Node.js 18+
- PHP 8+
- SQLite3

### Setup Instructions

1. **Clone Repository**
   ```bash
   git clone https://github.com/Sandeepsmvit/rdash.git
   cd rdash
   ```

2. **Install Dependencies**
   ```bash
   # Frontend
   npm install
   
   # Backend
   composer install
   ```

3. **Start Development Servers**
   ```bash
   # Terminal 1: Start PHP Backend
   php -S 127.0.0.1:8000 server/route.php
   
   # Terminal 2: Start Angular Frontend
   ng serve
   ```

4. **Access Application**
   - Frontend: http://localhost:4200
   - Backend API: http://localhost:8000

## 👥 Default Credentials

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@example.com | adminpass |
| Super Admin | superadmin@example.com | superpass |

## 📁 File Upload Limits

- **Images:** 5MB (JPG, PNG)
- **Videos:** 100MB (MP4, MOV, AVI)

## 🔧 Configuration

### Environment Variables
```bash
# Backend Configuration
PORT=8000
UPLOAD_PATH=/opt/render/project/src/server/uploads
MAX_PHOTO_SIZE=5242880
MAX_VIDEO_SIZE=104857600

# Frontend Configuration
NG_BUILD_COMMAND=ng build --configuration production --base-href /
```

## 🐛 Troubleshooting

### Common Issues

1. **CORS Errors**
   - Ensure backend CORS allows frontend URL
   - Check environment variables are set correctly

2. **File Upload Issues**
   - Verify upload directory permissions
   - Check file size limits in PHP configuration

3. **Database Issues**
   - Ensure SQLite database file exists
   - Check file permissions for database directory

### Health Checks

- **Backend Health:** `GET /route/health`
- **Frontend Status:** Check browser console for errors

## 📞 Support

For issues and questions:
- **GitHub Issues:** https://github.com/Sandeepsmvit/rdash/issues
- **Documentation:** Check this README and code comments

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

**Built with ❤️ using Angular, PHP, and Render**
