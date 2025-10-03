# Overview

Visionary AI is a comprehensive AI tools platform offering a suite of AI-powered image generation and manipulation capabilities. Built as a full-stack TypeScript application with a React frontend and Express.js backend, it provides features such as text-to-image generation, background removal, image upscaling, sketching, and image-to-image transformation. The platform aims to deliver a modern user experience with a dark-themed UI, community gallery, and efficient access to AI tools.

# Recent Changes

**October 3, 2025** - GitHub Import Successfully Configured for Replit:
- Fresh GitHub repository clone imported and configured for Replit environment
- All npm packages installed (630+ packages for full-stack TypeScript app)
- Workflow "Start application" configured to run on port 5000 with webview output
- Vite already properly configured with `allowedHosts: true` and host `0.0.0.0` for Replit proxy compatibility
- Express server serves both API (backend) and frontend on single port 5000
- Storage system with automatic fallback: Google Drive (primary) → In-Memory (fallback)
  - Currently using in-memory storage (Google Drive connector not connected)
  - Admin user (eeweed27ai@admin.com) automatically created at startup
- Application fully tested and verified working:
  - Frontend loads with dark-themed UI, sidebar navigation, tool buttons
  - Community Creations gallery visible with art style filters
  - All navigation working (Dashboard, Profile, Settings, Favorites, Art Styles, etc.)
- Deployment configured for autoscale with:
  - Build: `npm run build` (Vite frontend + ESBuild backend)
  - Run: `npm run start` (production server on port 5000)
- Note: AI image generation features require GOOGLE_API_KEY or GEMINI_API_KEY environment variable

**October 3, 2025** - Enhanced Admin Panel with Delete and Ban Features:
- Added admin capability to delete images from the database
- Added admin capability to delete user profiles
- Added admin capability to ban users (sets isBanned flag on user profiles)
- Added admin capability to unban users
- Updated userProfiles schema with isBanned boolean field (defaults to false)
- Implemented deleteImage, deleteUserProfile, banUser, unbanUser methods in all storage classes (DatabaseStorage, InMemoryStorage, GoogleDriveStorage)
- Added API routes: DELETE /api/admin/images/:id, DELETE /api/admin/users/:userId, PATCH /api/admin/users/:userId/ban, PATCH /api/admin/users/:userId/unban
- Enhanced Admin UI with:
  - Delete button (trash icon) for each image in Image Management
  - Status column in User Management showing Active/Banned badges
  - Actions column in User Management with Ban/Unban and Delete buttons
  - All actions include proper loading states and toast notifications
- All features include proper data-testid attributes for testing

**October 3, 2025** - Fresh GitHub Import & Google Drive Setup:
- Successfully imported GitHub repository to Replit environment
- PostgreSQL database provisioned but NOT in use per user preference
- Google Drive connector integrated and configured for data storage
- All data persists in Google Drive (VisionaryAI_Storage folder with database.json)
- Storage includes: users, images, art styles, profiles, custom models, admins
- Admin user (eeweed27ai@admin.com) automatically created at startup
- Workflow configured to run on port 5000 with webview output
- Vite properly configured with allowedHosts: true and host 0.0.0.0
- Application fully functional and tested - frontend loads, storage works
- Deployment configured for autoscale with npm run build and npm run start

**October 3, 2025** - Previous Google Drive Database Integration:
- Integrated Google Drive as the primary database storage using Replit's Google Drive connector
- Created GoogleDriveStorage class that implements full IStorage interface
- Data persists as JSON file (database.json) in VisionaryAI_Storage folder in Google Drive
- All data (users, images, art styles, profiles, custom models, admins) stored in Google Drive
- Automatic fallback to in-memory storage if Google Drive connection fails
- Admin user (eeweed27ai@admin.com) automatically created at startup
- Data survives app restarts - persisted to Google Drive
- Application fully functional with Google Drive storage - verified with successful API requests
- Note: Google API key warning expected - AI features require GOOGLE_API_KEY or GEMINI_API_KEY environment variable

**October 3, 2025** - Switched to Internal Storage System (superseded by Google Drive):
- Initially configured application to use internal in-memory storage
- Updated db.ts to gracefully handle missing DATABASE_URL without throwing errors

**October 3, 2025** - Fresh GitHub Import and Replit Environment Setup:
- Successfully imported fresh GitHub repository to Replit
- Installed all npm dependencies (610 packages) for full-stack TypeScript app
- Created comprehensive .gitignore file for Node.js project with build artifacts excluded
- Workflow "Start application" configured and running on port 5000 with webview output
- Verified Vite configuration already properly set up with `allowedHosts: true` and host `0.0.0.0` for Replit proxy
- Application tested and confirmed working - homepage loads with full UI, sidebar navigation, and community gallery
- Deployment configured for autoscale with build command and production start script

**October 2, 2025** - Admin Panel Implementation:
- Created comprehensive admin panel accessible at /admin route
- Added admins table to database schema to track administrator users
- Admin user created: email `eeweed27ai@admin.com`
- Implemented admin storage methods for checking admin status, managing images, users, and statistics
- Created admin API routes for:
  - Admin status verification
  - Image moderation (approve/reject images)
  - User profile management
  - Art styles browsing
  - Platform statistics dashboard
- Built feature-rich admin panel UI with four main sections:
  - Dashboard: Real-time statistics showing total images, users, art styles, and pending moderation count
  - Image Management: View all images, moderate content with approve/reject actions
  - User Management: Browse all user profiles with details
  - Art Styles: View all custom art styles created by users
- Admin panel link appears in sidebar only for authenticated admin users
- Admin panel uses shadcn/ui components with Table, Tabs, Cards, and Badges
- All features include proper data-testid attributes for testing
- Security: Admin checks performed server-side based on email in admins table

**October 1, 2025** - Comprehensive Guides & Tutorials Page:
- Created dedicated /guides page with complete documentation for all AI tools and features
- Implemented tabbed interface with three sections: AI Tools, Tips & Tricks, and Getting Started
- Each tool guide includes detailed "What it does", "How to use" steps, and pro tips
- Documented all AI tools: Text-to-Image, Image-to-Image, BG Remover, Upscaler, Image-to-Sketch, and Art Styles
- Added practical guidance on prompt crafting, troubleshooting, and getting best results
- Updated top navigation bar with link to guides page
- Used shadcn/ui Card and Tabs components for clean, accessible interface

**October 1, 2025** - Custom Model Image Generation Fix:
- Fixed critical bug where custom models (Hugging Face and custom APIs) were not generating images
- Standardized backend response format to `{ success: true, generatedImage: <data_url> }` for consistency
- Implemented robust content-type detection supporting application/json, text/plain, image/*, and application/octet-stream
- Added recursive image extraction from various API response formats (nested objects, arrays, common field names)
- Made API key optional for custom models to support public/keyless endpoints
- Added base64 normalization to ensure proper data URL format
- Note: SSRF security considerations documented for production deployment (URL validation, private IP blocking recommended)

**October 1, 2025** - GitHub Import to Replit Environment Setup:
- Successfully imported fresh GitHub clone and configured for Replit environment
- PostgreSQL database provisioned and schema synced using `npm run db:push`
- Updated dev script to use `npx tsx` for Replit compatibility
- Workflow "Start application" configured to run `npm run dev` on port 5000 with webview output
- Vite already properly configured with `allowedHosts: true` and host `0.0.0.0` for Replit proxy compatibility
- Firebase authentication configured with environment variable fallbacks for development
- Deployment configured for autoscale with build command `npm run build` and start command `npm run start`
- Build process verified working (frontend + backend bundles successfully)
- Application running successfully on port 5000 with no TypeScript or LSP errors
- All database tables created: users, images, saved_images, user_art_styles, user_profiles, custom_models
- Note: AI image generation features require GOOGLE_API_KEY or GEMINI_API_KEY environment variable to be set for Gemini 2.0 Flash Experimental model

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The frontend is built with React 18 and TypeScript, utilizing Tailwind CSS with shadcn/ui for styling, React Query for server state management, and Wouter for lightweight routing. Vite is used for fast development and optimized production builds.

## Backend Architecture
The backend uses Express.js with TypeScript, following a RESTful API design pattern. It operates on Node.js 18+ with ESM modules, features centralized route registration, global error handling, and custom logging middleware.

## Data Storage Solutions
The application employs a flexible storage abstraction, primarily using PostgreSQL with Drizzle ORM for persistent storage. An automatic fallback to in-memory storage is implemented if the database is unavailable. Drizzle Kit is used for type-safe database schema management and migrations.

## Authentication and Authorization
Firebase Authentication is integrated for comprehensive user management, supporting email/password and Google OAuth. Firebase token-based authentication handles sessions, and React hooks manage authentication state.

## Component Design System
A comprehensive UI component library, built on Radix UI primitives and shadcn/ui components, ensures consistent styling. It features a dark mode theme system using CSS variables, and uses Inter and Space Grotesk fonts. The design adopts a mobile-first approach with Tailwind breakpoints.

# External Dependencies

## Database and Storage
- **Drizzle ORM**: Type-safe database queries and schema management.
- **PostgreSQL**: Primary database (via @neondatabase/serverless driver).
- **Drizzle Kit**: Database migration and introspection tools.

## Authentication Services
- **Firebase Authentication**: User authentication and management.
- **Google OAuth**: Social login integration.
- **Firebase SDK**: Client-side authentication handling.

## UI and Frontend Libraries
- **Radix UI**: Headless UI primitives.
- **Tailwind CSS**: Utility-first CSS framework.
- **Lucide React**: Icon library.
- **React Hook Form**: Form state management and validation.
- **TanStack React Query**: Server state management and caching.

## Development and Build Tools
- **Vite**: Frontend build tool and development server.
- **TypeScript**: Type safety across frontend and backend.
- **ESBuild**: Backend bundling for production.

## Third-party Integrations
- **Unsplash/Pixabay**: Stock images for gallery placeholder content.
- **Google Fonts**: Web font loading.
- **Social Media**: Links to Telegram, Twitter, Instagram, and Discord communities.