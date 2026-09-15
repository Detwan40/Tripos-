# Tripos - Nomad Travel Agency Booking Platform

A comprehensive web application that allows travelers to book flights, accommodations, activities, and car rentals all in one place.

## Features

- **Flight Booking** - Search and book flights across multiple airlines
- **Accommodation Booking** - Reserve hotels, hostels, and vacation rentals
- **Activity Booking** - Browse and book tours, experiences, and adventures
- **Car Rental Booking** - Reserve vehicles for your destination
- **Unified Checkout** - Book everything in a single transaction
- **User Accounts** - Save bookings, preferences, and travel history
- **Payment Processing** - Secure payment integration
- **Itinerary Management** - Organize and view all bookings in one place

## Tech Stack

### Frontend
- React.js / Next.js
- TypeScript
- Tailwind CSS
- Redux or Zustand for state management

### Backend
- Node.js with Express
- PostgreSQL / MongoDB
- JWT authentication
- RESTful API design

### Third-Party Integrations
- Payment gateway (Stripe/PayPal)
- Flight APIs (Amadeus/Skyscanner)
- Hotel APIs (Booking.com/Expedia)
- Maps (Google Maps)

## Project Structure

```
Tripos-/
├── frontend/          # React/Next.js application
├── backend/           # Node.js API server
├── database/          # Database schemas and migrations
├── docs/              # Documentation
└── .github/workflows/ # CI/CD pipelines
```

## Getting Started

### Prerequisites
- Node.js 18+
- npm or yarn
- PostgreSQL 12+
- Git

### Installation

1. Clone the repository
```bash
git clone https://github.com/Detwan40/Tripos-.git
cd Tripos-
```

2. Install dependencies
```bash
# Frontend
cd frontend
npm install

# Backend
cd ../backend
npm install
```

3. Set up environment variables
```bash
cp .env.example .env
```

4. Run development servers
```bash
# Terminal 1: Backend
cd backend
npm run dev

# Terminal 2: Frontend
cd frontend
npm run dev
```

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

## License

MIT License - see LICENSE file for details

## Live Demo

https://tripos-iota.vercel.app
