# Database Schema

## Tables

### users
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  phone VARCHAR(20),
  profile_picture_url TEXT,
  preferred_currency VARCHAR(3) DEFAULT 'USD',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### bookings
```sql
CREATE TABLE bookings (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id),
  booking_reference VARCHAR(20) UNIQUE NOT NULL,
  total_price DECIMAL(10, 2),
  currency VARCHAR(3),
  status VARCHAR(50) DEFAULT 'pending',
  payment_status VARCHAR(50) DEFAULT 'pending',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### booking_flights
```sql
CREATE TABLE booking_flights (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  booking_id UUID REFERENCES bookings(id),
  flight_id VARCHAR(255),
  departure_airport VARCHAR(10),
  arrival_airport VARCHAR(10),
  departure_time TIMESTAMP,
  arrival_time TIMESTAMP,
  price DECIMAL(10, 2),
  seats INTEGER,
  airline VARCHAR(100),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### booking_hotels
```sql
CREATE TABLE booking_hotels (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  booking_id UUID REFERENCES bookings(id),
  hotel_id VARCHAR(255),
  hotel_name VARCHAR(255),
  check_in_date DATE,
  check_out_date DATE,
  price DECIMAL(10, 2),
  rooms INTEGER,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### booking_activities
```sql
CREATE TABLE booking_activities (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  booking_id UUID REFERENCES bookings(id),
  activity_id VARCHAR(255),
  activity_name VARCHAR(255),
  activity_date DATE,
  activity_time TIME,
  price DECIMAL(10, 2),
  participants INTEGER,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### booking_cars
```sql
CREATE TABLE booking_cars (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  booking_id UUID REFERENCES bookings(id),
  car_id VARCHAR(255),
  car_type VARCHAR(100),
  pickup_date DATE,
  return_date DATE,
  pickup_location VARCHAR(255),
  return_location VARCHAR(255),
  price DECIMAL(10, 2),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Indexes

```sql
CREATE INDEX idx_bookings_user_id ON bookings(user_id);
CREATE INDEX idx_bookings_status ON bookings(status);
CREATE INDEX idx_booking_flights_booking_id ON booking_flights(booking_id);
CREATE INDEX idx_booking_hotels_booking_id ON booking_hotels(booking_id);
CREATE INDEX idx_booking_activities_booking_id ON booking_activities(booking_id);
CREATE INDEX idx_booking_cars_booking_id ON booking_cars(booking_id);
```
