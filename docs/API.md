# Tripos API Documentation

## Base URL
```
http://localhost:5000/api/v1
```

## Authentication

All endpoints (except login/register) require Bearer token authentication:
```
Authorization: Bearer <token>
```

## Core Endpoints

### Flights
- `GET /flights/search` - Search available flights
- `GET /flights/:id` - Get flight details
- `POST /bookings/flights` - Book a flight

### Hotels
- `GET /hotels/search` - Search available hotels
- `GET /hotels/:id` - Get hotel details
- `POST /bookings/hotels` - Book a hotel

### Activities
- `GET /activities/search` - Search activities
- `GET /activities/:id` - Get activity details
- `POST /bookings/activities` - Book an activity

### Cars
- `GET /cars/search` - Search rental cars
- `GET /cars/:id` - Get car details
- `POST /bookings/cars` - Book a car

### Bookings
- `GET /bookings` - Get user's bookings
- `GET /bookings/:id` - Get booking details
- `POST /bookings` - Create unified booking
- `PUT /bookings/:id` - Update booking
- `DELETE /bookings/:id` - Cancel booking

### Users
- `POST /auth/register` - Register new user
- `POST /auth/login` - Login user
- `GET /profile` - Get user profile
- `PUT /profile` - Update profile

## Error Responses

```json
{
  "success": false,
  "message": "Error description",
  "errorCode": "ERROR_CODE",
  "statusCode": 400
}
```

## Rate Limiting

- Limit: 1000 requests per hour per user
- Headers: `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset`
