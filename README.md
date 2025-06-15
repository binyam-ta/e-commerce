# Event Ticketing App - Next.js & MongoDB


A full-stack event ticketing application built with Next.js (TypeScript) and MongoDB, featuring user authentication, event management, ticket purchasing, and QR code validation.

## Features

###  Authentication & User Roles
- User registration & login with JWT
- Role-based access control:
  - Guest: Browse events
  - User: Buy tickets
  - Organizer: Create/manage events
  - Admin: Full system control

###  Event Management
- Browse events with search/filters
- Create/edit/delete events (Organizers)
- Set ticket limits and pricing
- Filter by date, location, price, category

###  Ticketing System
- Mock checkout process
- One ticket per user per event
- Unique QR code generation
- Ticket usage tracking
- Prevent duplicate purchases

###  Dashboard
- Organizer dashboard:
  - View owned events
  - Track ticket sales
  - See attendees list
- Admin panel (optional):
  - Manage users and events
  - Promote/demote organizers

## Tech Stack

### Frontend
- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **UI**: Tailwind CSS
- **State Management**: React Context + SWR
- **QR Generation**: qrcode.react

### Backend
- **Runtime**: Node.js
- **Framework**: Next.js API Routes
- **Database**: MongoDB (Mongoose ODM)
- **Authentication**: JWT with HTTP-only cookies
- **Password Hashing**: bcryptjs

### Development
- **Environment Variables**: .env.local
- **Linting**: ESLint + Prettier
- **Version Control**: Git

## Getting Started

### Prerequisites
- Node.js v18+
- MongoDB Atlas account or local MongoDB instance
- Git

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/event-ticketing-app.git
   cd event-ticketing-app
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up environment variables**:
   Create `.env.local` file in root directory:
   ```env
   MONGODB_URI="your_mongodb_connection_string"
   JWT_SECRET="your_strong_jwt_secret_here"
   ```

4. **Run the development server**:
   ```bash
   npm run dev
   ```

5. **Open in your browser**:
   Visit `http://localhost:3000`

### Database Setup
The application will automatically create the following collections:
- `users` - User accounts
- `events` - Event listings
- `tickets` - Ticket records

## Project Structure

```
event-ticketing-app/
├── app/                   # Next.js App Router
│   ├── (auth)/            # Authentication routes
│   ├── (user)/            # User dashboard
│   ├── (organizer)/       # Organizer dashboard
│   ├── (admin)/           # Admin panel (optional)
│   ├── events/            # Event pages
│   └── api/               # API routes
│       ├── auth/          # Auth endpoints
│       ├── events/        # Event endpoints
│       └── tickets/       # Ticket endpoints
├── components/            # Reusable UI components
├── context/               # React context providers
├── lib/                   # Utility functions
├── models/                # Mongoose models
├── public/                # Static assets
├── styles/                # Global styles
├── .env.local             # Environment variables
├── package.json
└── README.md
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user

### Events
- `GET /api/events` - Get all events
- `GET /api/events/[id]` - Get single event
- `POST /api/events/create` - Create new event (Organizer)
- `PUT /api/events/[id]` - Update event (Organizer)

### Tickets
- `POST /api/tickets/buy` - Purchase ticket
- `GET /api/tickets/[userId]` - Get user's tickets
- `POST /api/tickets/validate` - Validate ticket (QR scan)

## Deployment

The application can be deployed to Vercel with minimal configuration:

1. Push your code to a Git repository
2. Create a new project in Vercel and connect your repository
3. Add environment variables in Vercel dashboard:
   - `MONGODB_URI`
   - `JWT_SECRET`
4. Deploy!

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Create a new Pull Request

