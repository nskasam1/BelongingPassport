# YMCA Volunteering App

A full-stack authentication application built with Next.js and Firebase, featuring role-based access control with three distinct user roles.

Check out our DevPost!
https://devpost.com/software/ymca-future-for-data-2025?ref_content=existing_user_added_to_software_team&ref_feature=portfolio&ref_medium=email&utm_campaign=software&utm_content=added_to_software_team&utm_medium=email&utm_source=transactional#app-team

## Features

- **Role-Based Authentication**: Three user roles (Primary Admin, Staff, Volunteers)
- **Firebase Integration**: Secure authentication and user data storage
- **Protected Routes**: Role-specific access control
- **Modern UI**: Built with Tailwind CSS
- **TypeScript**: Full type safety throughout the application

## User Roles

1. **Primary Admin**: Full system access with user management capabilities
2. **Staff**: Management access with volunteer coordination features
3. **Volunteers**: Basic access with activity tracking

## Tech Stack

- **Frontend**: Next.js 14 with App Router
- **Backend**: Firebase Authentication & Firestore
- **Styling**: Tailwind CSS
- **Language**: TypeScript
- **State Management**: React Context API

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn
- Firebase project

### Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd future-of-data-2025
```

2. Install dependencies:
```bash
npm install
```

3. Set up Firebase:
   - Create a new Firebase project at [Firebase Console](https://console.firebase.google.com/)
   - Enable Authentication (Email/Password)
   - Enable Firestore Database
   - Get your Firebase configuration

4. Configure environment variables:
   - Copy `.env.local.example` to `.env.local`
   - Add your Firebase configuration:

```env
NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key_here
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project_id.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project_id.appspot.com
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
```

5. Run the development server:
```bash
npm run dev
```

6. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
src/
├── app/                    # Next.js App Router pages
│   ├── auth/              # Authentication pages
│   ├── dashboard/         # Protected dashboard
│   ├── layout.tsx         # Root layout with AuthProvider
│   └── page.tsx           # Home page
├── components/            # React components
│   ├── auth/              # Authentication components
│   └── dashboard/         # Dashboard components
├── contexts/              # React contexts
│   └── AuthContext.tsx    # Authentication context
├── lib/                   # Utility libraries
│   └── firebase.ts        # Firebase configuration
└── types/                 # TypeScript type definitions
    └── auth.ts            # Authentication types
```

## Usage

### Authentication Flow

1. **Sign Up**: Users can register with email, password, display name, and role
2. **Sign In**: Users can sign in with their credentials
3. **Role-Based Access**: Users are redirected to role-specific dashboards
4. **Protected Routes**: Access is controlled based on user roles

### Creating Users

1. Visit `/auth` to access the authentication page
2. Toggle to "Create account" mode
3. Fill in the registration form with:
   - Full Name
   - Email Address
   - Role (Primary Admin, Staff, or Volunteer)
   - Password
   - Confirm Password

### Accessing Dashboards

- **Primary Admin**: Full system access with user management
- **Staff**: Volunteer management and event coordination
- **Volunteers**: Personal activity tracking and event participation

## Firebase Setup

### Authentication Setup

1. Go to Firebase Console → Authentication
2. Enable "Email/Password" sign-in method
3. Configure any additional settings as needed

### Firestore Setup

1. Go to Firebase Console → Firestore Database
2. Create a new database
3. Set up security rules (example provided below)

### Firestore Security Rules

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Users can read and write their own user document
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint

### Adding New Features

1. **New User Roles**: Update the `UserRole` type in `src/types/auth.ts`
2. **New Protected Routes**: Add routes to the `ProtectedRoute` component
3. **New Dashboard Features**: Create components in `src/components/dashboard/`
