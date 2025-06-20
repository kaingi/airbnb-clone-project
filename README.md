     Team Roles
Backend Developer: Responsible for implementing API endpoints, database schemas, and business logic.
Database Administrator: Manages database design, indexing, and optimizations.
DevOps Engineer: Handles deployment, monitoring, and scaling of the backend services.
QA Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.

     Technology Stack
Django: A high-level Python web framework used for building the RESTful API.
Django REST Framework: Provides tools for creating and managing RESTful APIs.
PostgreSQL: A powerful relational database used for data storage.
GraphQL: Allows for flexible and efficient querying of data.
Celery: For handling asynchronous tasks such as sending notifications or processing payments.
Redis: Used for caching and session management.
Docker: Containerization tool for consistent development and deployment environments.
CI/CD Pipelines: Automated pipelines for testing and deploying code changes.


    Database Design
🔑 Key Entities, Fields, and Relationships
1. Users
- Represents individuals using the platform, either as guests or hosts.

Important Fields:

*user_id: Unique identifier

*name: Full name of the user

*email: Contact email

*role: Indicates whether the user is a "host" or "guest"

*created_at: Account creation timestamp

Relationships:

*A user can be a host of many properties.

*A user (as a guest) can make multiple bookings.

*A user can leave multiple reviews.

*A user can make multiple payments.

2. Properties
- Represents rental listings posted by hosts.

Important Fields:

*property_id: Unique identifier

*title: Name of the property

*description: Overview of the property

*location: Physical address or region

*host_id: Refers to the user who owns the property

Relationships:

*A property belongs to one host (user).

*A property can receive many bookings.

*A property can have multiple reviews.

3. Bookings
-Represents reservations made by guests for specific properties.

Important Fields:

*booking_id: Unique identifier

*user_id: Guest who made the booking

*property_id: Booked property

*start_date & end_date: Booking duration

*status: Booking state (e.g., confirmed, cancelled)

Relationships:

*A booking is made by a guest (user).

*A booking is associated with one property.

*A booking can have one payment.

4. Reviews
-Represents guest feedback about a property after their stay.

Important Fields:

*review_id: Unique identifier

*user_id: Guest who wrote the review

*property_id: Reviewed property

*rating: Numeric score (e.g., 1–5)

*comment: Written feedback

Relationships:

*A review is written by a user.

*A review is associated with one property.

5. Payments
-Tracks transactions made by users for their bookings.

Important Fields:

*payment_id: Unique identifier

*booking_id: Related booking

*user_id: Guest making the payment

*amount: Payment amount

*payment_date: Date of payment

Relationships:

*A payment is made by a user.

*A payment is linked to one booking.

🔗 Summary of Relationships
*User → can own multiple → Properties

*User → can make multiple → Bookings

*User → can write multiple → Reviews

*User → can make multiple → Payments

*Property → belongs to one → User (host)

*Property → has multiple → Bookings

*Property → has multiple → Reviews

*Booking → belongs to one → User (guest)

*Booking → belongs to one → Property

*Booking → has one → Payment

*Review → belongs to one → User

*Review → belongs to one → Property

*Payment → belongs to one → Booking

*Payment → belongs to one → User
