# Portfolio & Blog Frontend

A modern, responsive React application for managing your portfolio and blog, featuring a beautiful pink-themed UI inspired by iOS and HarmonyOS design.

## Table of Contents

- [Live Demo](#live-demo)
- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Local Development Setup](#local-development-setup)
- [Connecting to Backend API](#connecting-to-backend-api)
- [Project Structure](#project-structure)
- [Pages](#pages)
- [Deployment](#deployment)

---

## Live Demo

### Online Sites

**🌐 Frontend Application:**
https://frontend-7um8ncxze-news-projects-3dedff93.vercel.app

**🔗 Backend API:**
https://portfolio-blog-api-tr0r.onrender.com/api

**📚 Backend Repository:**
https://github.com/aaaazzz222/backend

---

## Project Overview

This is a full-stack portfolio and blog application built with the MERN stack (MongoDB, Express, React, Node.js). The frontend provides a beautiful, user-friendly interface for showcasing projects, publishing blog posts, and managing content through an admin dashboard.

### Key Highlights

- **Modern UI/UX**: Beautiful pink color scheme with smooth animations
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- **Full Authentication**: Secure JWT-based authentication system
- **Admin Dashboard**: Complete content management system
- **Blog System**: Full-featured blog with commenting functionality
- **Portfolio Showcase**: Display your projects with images and links

---

## Features

### User Features
- ✅ **Beautiful Pink Theme** - iOS/HarmonyOS inspired design
- ✅ **Responsive Design** - Mobile-first approach, works on all devices
- ✅ **Authentication** - Secure user registration and login
- ✅ **Portfolio Gallery** - Browse through all projects
- ✅ **Blog Reading** - Read blog posts with full content
- ✅ **Comment System** - Authenticated users can comment on posts
- ✅ **Contact Form** - Easy way to get in touch

### Admin Features
- ✅ **Admin Dashboard** - Centralized content management
- ✅ **Project Management** - Create, edit, and delete projects
- ✅ **Blog Management** - Create, edit, and delete blog posts
- ✅ **Message Viewing** - View all contact form submissions
- ✅ **Protected Routes** - Secure admin-only access

---

## Tech Stack

### Core Technologies
- **React** 19.2.0 - Latest React with modern features
- **React Router** 7.9.6 - Client-side routing
- **Axios** 1.13.2 - HTTP client for API calls
- **Vite** 7.2.2 - Ultra-fast build tool and dev server

### State Management
- **Context API** - Global authentication state
- **Local State** - Component-level state with hooks

### Development Tools
- **ESLint** - Code linting and formatting
- **Vite** - Fast HMR (Hot Module Replacement)

---

## Local Development Setup

### Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v16 or higher) - [Download here](https://nodejs.org/)
- **npm** (comes with Node.js) or **yarn**
- **Git** - [Download here](https://git-scm.com/)

### Step 1: Clone the Repository

```bash
# Clone this repository
git clone https://github.com/aaaazzz222/frontend.git

# Navigate to the project directory
cd frontend
```

### Step 2: Install Dependencies

```bash
# Install all required packages
npm install
```

This will install all dependencies listed in `package.json`.

### Step 3: Configure Environment Variables

Create a `.env` file in the root directory:

```bash
# Create .env file
touch .env
```

Add the following content to `.env`:

#### For Local Development:
```env
VITE_API_URL=http://localhost:4000/api
```

#### For Production (using deployed backend):
```env
VITE_API_URL=https://portfolio-blog-api-tr0r.onrender.com/api
```

**Note:** The `VITE_` prefix is required for Vite to expose the variable to your application.

### Step 4: Start Development Server

```bash
# Start the development server
npm run dev
```

The application will open at `http://localhost:5173` (or another available port).

### Step 5: Build for Production

```bash
# Create production build
npm run build

# Preview production build locally
npm run preview
```

The build files will be generated in the `dist` directory.

---

## Connecting to Backend API

### Local Backend Setup

To connect to a local backend during development:

1. **Clone and setup the backend:**
   ```bash
   # Clone the backend repository
   git clone https://github.com/aaaazzz222/backend.git

   # Navigate to backend directory
   cd backend

   # Install dependencies
   npm install

   # Create .env file with MongoDB connection
   # See backend README for details

   # Start backend server
   npm run dev
   ```

2. **Configure frontend to use local backend:**

   Update your `.env` file:
   ```env
   VITE_API_URL=http://localhost:4000/api
   ```

3. **Verify connection:**

   The frontend will automatically connect to the backend API. Check the browser console for any connection errors.

### Using Production Backend

If you prefer to use the deployed backend API:

1. Update your `.env` file:
   ```env
   VITE_API_URL=https://portfolio-blog-api-tr0r.onrender.com/api
   ```

2. No additional setup required - the frontend will connect to the production API.

### API Configuration File

The API base URL is configured in `src/services/api.js`:

```javascript
import axios from 'axios';

const API_URL = import.meta.env.VITE_API_URL || 'http://localhost:4000/api';

export default axios.create({
  baseURL: API_URL,
  headers: {
    'Content-Type': 'application/json',
  },
});
```

### Troubleshooting API Connection

If you encounter connection issues:

1. **Check if backend is running:**
   ```bash
   curl http://localhost:4000/api
   ```

2. **Verify environment variable:**
   ```bash
   echo $VITE_API_URL
   ```

3. **Check browser console** for CORS or network errors

4. **Ensure CORS is enabled** in the backend (it should be by default)

---

## Project Structure

```
frontend/
├── public/              # Static assets
├── src/
│   ├── components/      # Reusable components
│   │   ├── Header.jsx        # Navigation bar
│   │   ├── Footer.jsx        # Footer component
│   │   └── ProtectedRoute.jsx # Route guard
│   ├── pages/           # Page components
│   │   ├── Home.jsx          # Homepage
│   │   ├── Projects.jsx      # Projects gallery
│   │   ├── Blog.jsx          # Blog list
│   │   ├── BlogPost.jsx      # Single blog post
│   │   ├── Contact.jsx       # Contact form
│   │   ├── Login.jsx         # Login page
│   │   ├── Register.jsx      # Registration page
│   │   └── AdminDashboard.jsx # Admin panel
│   ├── context/         # Context providers
│   │   └── AuthContext.jsx   # Authentication context
│   ├── services/        # API services
│   │   └── api.js            # Axios instance
│   ├── App.jsx          # Main app component
│   ├── main.jsx         # Entry point
│   └── index.css        # Global styles
├── .env                 # Environment variables
├── .env.production      # Production environment variables
├── .gitignore          # Git ignore rules
├── package.json        # Dependencies and scripts
├── vite.config.js      # Vite configuration
└── README.md           # This file
```

---

## Pages

### Public Pages (No Authentication Required)

#### 1. Home (`/`)
- Welcome page with introduction
- Quick navigation to other sections
- Hero section with call-to-action

#### 2. Projects (`/projects`)
- Gallery of all portfolio projects
- Each project shows:
  - Title and description
  - Project image
  - GitHub repository link
  - Live demo link

#### 3. Blog (`/blog`)
- List of all blog posts
- Shows title, excerpt, and date
- Click to read full post

#### 4. Blog Post (`/blog/:id`)
- Full blog post content
- Author information
- Comments section
- Add comment (requires login)

#### 5. Contact (`/contact`)
- Contact form with:
  - Name
  - Email
  - Message
- Form validation
- Success/error feedback

#### 6. Login (`/login`)
- User login form
- Email and password fields
- Link to registration
- JWT token authentication

#### 7. Register (`/register`)
- New user registration
- Username, email, and password
- Input validation
- Auto-login after registration

### Protected Pages (Authentication Required)

#### 8. Admin Dashboard (`/admin`)
- **Access**: Requires authentication
- **Features**:
  - Create new projects
  - Edit/delete existing projects
  - Create new blog posts
  - Edit/delete blog posts
  - View contact messages

---

## Design System

### Color Palette

The application features a beautiful pink theme:

```css
Primary: #FF6B9D
Primary Light: #FFB3D9
Primary Dark: #E63980
Secondary: #FFC2D1
Accent: #FF9EBB
Background: #FFFFFF
Text: #333333
```

### Design Principles

- **Minimalist**: Clean, uncluttered interface
- **Responsive**: Mobile-first design approach
- **Accessible**: High contrast ratios for readability
- **Smooth**: Transitions and animations
- **Modern**: Card-based layouts

### Typography

- **Headings**: Bold, clear hierarchy
- **Body**: Readable font size and line height
- **Code**: Monospace font for technical content

---

## Authentication

### How It Works

1. **Registration/Login**
   - User enters credentials
   - Backend validates and returns JWT token
   - Token is stored in localStorage
   - AuthContext provides global access

2. **Protected Routes**
   - ProtectedRoute component checks for valid token
   - Redirects to login if not authenticated
   - Allows access if authenticated

3. **API Requests**
   - Token is included in Authorization header
   - Backend validates token for protected endpoints

### User Permissions

**Public Users Can:**
- View all projects
- Read all blog posts
- View comments
- Submit contact form

**Authenticated Users Can:**
- All public permissions
- Post comments on blog posts
- Access admin dashboard
- Create/edit/delete projects
- Create/edit/delete blog posts
- View contact messages

---

## Deployment

### Deploy to Vercel (Recommended)

1. **Push code to GitHub**

2. **Connect to Vercel:**
   - Go to [vercel.com](https://vercel.com)
   - Import your repository
   - Configure project

3. **Set Environment Variables:**
   ```
   VITE_API_URL=https://portfolio-blog-api-tr0r.onrender.com/api
   ```

4. **Deploy:**
   - Build command: `npm run build`
   - Output directory: `dist`
   - Framework preset: Vite

### Deploy to Netlify

1. **Build settings:**
   - Build command: `npm run build`
   - Publish directory: `dist`

2. **Environment variables:**
   ```
   VITE_API_URL=https://portfolio-blog-api-tr0r.onrender.com/api
   ```

3. **Deploy**

---

## Available Scripts

### Development

```bash
# Start development server with hot reload
npm run dev
```

### Production Build

```bash
# Create optimized production build
npm run build
```

### Preview Production Build

```bash
# Preview the production build locally
npm run preview
```

### Linting

```bash
# Run ESLint to check code quality
npm run lint
```

---

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

---

## Troubleshooting

### Common Issues

1. **Port already in use:**
   ```bash
   # Vite will automatically try another port
   # Or specify a custom port:
   npm run dev -- --port 3000
   ```

2. **API connection failed:**
   - Check if backend is running
   - Verify VITE_API_URL in .env
   - Check browser console for errors

3. **Build fails:**
   ```bash
   # Clear node_modules and reinstall
   rm -rf node_modules package-lock.json
   npm install
   ```

4. **Changes not reflecting:**
   - Hard refresh browser (Cmd/Ctrl + Shift + R)
   - Clear browser cache
   - Restart dev server

---

## Performance

- **Vite HMR**: Instant updates during development
- **Code Splitting**: Automatic route-based code splitting
- **Lazy Loading**: Components loaded on demand
- **Optimized Build**: Minified and compressed production build

---

## Security

- **JWT Authentication**: Secure token-based auth
- **Protected Routes**: Client-side route protection
- **Input Validation**: Form input sanitization
- **HTTPS**: Secure communication in production
- **Environment Variables**: Sensitive data in .env

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## License

This project is open source and available under the MIT License.

---

## Support

For issues or questions:
- Create an issue in this repository
- Check the backend repository: https://github.com/aaaazzz222/backend

---

## Acknowledgments

- React team for the amazing framework
- Vite for the blazing-fast build tool
- All contributors and supporters

---

**Last Updated:** 2025-11-19
**Version:** 1.0.0

---

**Happy Coding!** 🚀✨
