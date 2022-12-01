# Booking System
Here we design a hotel reservation system for a hotel chain. The design is also applicable to other popular booking-related topics such as-
    Design AirBnb
    Design Flight Reservation System
    Design a movie booking system

## Requirements
### Functional Requirements
1. For Hotel Staff
    - Hotel Related
        * Add new hotel
        * Update hotel information
        * Delete a hotel
    - Room Related
        * Add a room
        * Update room details
        * Delete a room
    - Booking Related
        * Make reservation
        * Analytics
2. For end users
    - Hotel Related
        * Search Hotels
        * Get Hotel Information
    - Room Related
        * Get Room Information
    - Booking Related
        * Make reservation
        * Check all reservations
### Non-functional Requirements
- Support high concurrency. During peak season or big events, some hotels may have a lot of customers trying to book the same room.
- Moderate Latency. Its ideal to have a fast response time when user makes the reservation, but its acceptable if the system takes a few seconds to process the request.

## Scale
Lets assume we are building this for a hotel chain which has 5,000 hotels and 1 million rooms in total.

## High Level System Design
1. List of services needed:
    - Hotel Service
    - Rate Service
    - Search Service
    - Booking Service
    - Payment Service





