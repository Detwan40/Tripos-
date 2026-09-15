# Tripos Architecture

## System Overview

```
┌────────────────────────────────────────────────────────────┐
│                    Frontend (Next.js)                    │
│              React Components & Pages                   │
└────────────────────────────┬────────────────────────────────┘
                             │
                             │ HTTP/REST
                             │
┌────────────────────────────┴────────────────────────────────┐
│                  Backend (Node.js)                       │
│         Express Server & API Routes                      │
└────────────────────────────┬────────────────────────────────┘
                             │
         ┌───────────────────┼───────────────────┐
         │                   │                   │
    ┌────┴───────┐  ┌────────┴─────┐  ┌─────────┴────────┐
    │   Database │  │  Cache      │  │ Services        │
    │ (Postgres) │  │ (Redis)     │  │  (APIs)        │
    └────────────┘  └─────────────┘  └────────────────┘
```

## Component Architecture

### Frontend Layers
- **Pages**: Next.js pages (Search, Booking, Checkout)
- **Components**: Reusable React components
- **Services**: API client calls
- **State**: Redux/Zustand state management
- **Hooks**: Custom React hooks
- **Utils**: Helper functions

### Backend Layers
- **Routes**: HTTP endpoints
- **Controllers**: Request handlers
- **Services**: Business logic
- **Models**: Database models
- **Middleware**: Authentication, validation
- **Utils**: Helpers

## Data Flow

1. **Search Phase**
   - User enters search criteria
   - Frontend sends search query to backend
   - Backend queries third-party APIs
   - Results cached for performance
   - Frontend displays results

2. **Selection Phase**
   - User selects flights, hotels, activities, cars
   - Frontend stores selections in state
   - Real-time price updates

3. **Checkout Phase**
   - User reviews entire itinerary
   - Unified pricing calculation
   - Payment processing
   - Booking confirmation

## Security Considerations

- JWT authentication for all protected routes
- HTTPS only communication
- SQL injection prevention via parameterized queries
- XSS protection with sanitized inputs
- CORS configuration
- Rate limiting
- Password hashing with bcrypt
