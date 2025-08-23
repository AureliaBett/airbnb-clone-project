# airbnb-clone-project

## The Project overview
The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security.

### Goals of the project
User Management: Implement a secure system for user registration, authentication, and profile management.

Property Management: Develop features for property listing creation, updates, and retrieval.

Booking System: Create a booking mechanism for users to reserve properties and manage booking details

Payment Processing: Integrate a payment system to handle transactions and record payment details.

Review System: Allow users to leave reviews and ratings for properties.

Data Optimization: Ensure efficient data retrieval and storage through database optimizations.

### Tech Stack
Django, MySQL, and GraphQL

## Team Roles
Business Analyst: understands customer business needs and translates customer needs into requiremets

Product Owner: Hold responbility for a product vision and evolution, makes sure the final product meets the cusromers requirements

Project Manager: makes sure a product or part qs delivered on time and within budget

UI/UX designer: transforms a product vision into a user friendly design

Software developer: Engineers and stabilizes he product

Software Architect: Designs high level software architecture

Qaulity Assurance Engineer: Makes sure applications perfom according to requirements.

Test automation engineer: designs a test automation ecosystem

DevOps Engineer: facilitates cooperation between develeopment and operations teams

## Technology Stack

Django: A high-level Python web framework used for building the RESTful API.

Django REST Framework: Provides tools for creating and managing RESTful APIs.

PostgreSQL: A powerful relational database used for data storage.

GraphQL: Allows for flexible and efficient querying of data.

Celery: For handling asynchronous tasks such as sending notifications or processing payments.

Redis: Used for caching and session management.

Docker: Containerization tool for consistent development and deployment environments.

CI/CD Pipelines: Automated pipelines for testing and deploying code changes

## Database Design
### User 
Fields:
user_id (Primary Key, unique identifier)

name (Full name of the user)

email (Unique contact/login)

role (e.g., "Host" or "Guest")

created_at (Date joined)

Notes: A User can be a Host (owns properties) or a Guest (makes bookings).
One user account could technically do both.
### Property
Fields
property_id (Primary Key)

owner_id (FK → User)

title (Name of the property, e.g., "Cozy Apartment")

location (Address or city)

price_per_night (Rental cost)

Notes: A property belongs to one User (Host).
A user (host) can have many properties.
### Booking
Fields

booking_id (Primary Key)

property_id (FK → Property)

guest_id (FK → User)

check_in (Start date)

check_out (End date)

status (Pending, Confirmed, Canceled, Completed)

Notes
A booking belongs to one Property and one Guest. A property can have many bookings, but they must not overlap in time.
### Paymenent

Fields
payment_id (Primary Key)

booking_id (FK → Booking)

amount (Total cost paid)

status (Pending, Paid, Refunded, Failed)

payment_date (Timestamp of transaction)

Notes: A payment belongs to one booking. A booking can only have one successful payment, but could have multiple attempts.

### Review
Fields

review_id (Primary Key)

booking_id (FK → Booking)

user_id (FK → User who wrote the review)

rating (1–5 stars)

comment (Text feedback)

Notes: A review is linked to a Booking (ensures only verified guests review). A user (guest) writes the review, but it’s tied to both the property and the host indirectly.
## Feature Breakdown
### User Management
The platform allows users to register, log in, and manage their profiles. Users can act as hosts (listing properties) or guests (booking stays), enabling flexibility in platform participation.

### Property Management
Hosts can list their properties with details such as title, location, price per night, and availability. This feature ensures that properties are discoverable and provides potential guests with enough information to make booking decisions.

### Booking System
Guests can book available properties by selecting check-in and check-out dates. The booking system prevents overlapping reservations and keeps track of booking status (pending, confirmed, canceled, completed).

### Reviews and Ratings
Guests can leave reviews and star ratings for properties they have booked. This fosters trust in the platform by helping future guests make informed decisions and encouraging hosts to maintain high standards.

### Payment Processing
Payments are linked to bookings, ensuring secure transactions between guests and hosts. This feature manages payment statuses (pending, paid, refunded, failed) and ensures that bookings are only confirmed upon successful payment.

## API Security
### Authentication

APIs will use secure authentication methods (e.g., JWT or OAuth 2.0) to verify user identities before granting access. This prevents unauthorized access and ensures that only registered users can interact with the system.

### Authorization

Role-based access control (RBAC) will be enforced so that users can only perform actions relevant to their role (e.g., hosts managing properties, guests making bookings). This protects sensitive operations, such as editing property listings or processing payments.

### Rate Limiting & Throttling

API endpoints will have request limits to prevent abuse through brute-force attacks or denial-of-service (DoS) attempts. This ensures system stability and fair usage across all users.

### Data Encryption

All sensitive data, including login credentials and payment information, will be encrypted in transit (via HTTPS/TLS) and at rest where necessary. This helps protect user privacy and secures financial transactions.

### Input Validation & Sanitization

APIs will validate and sanitize incoming data to prevent injection attacks (e.g., SQL injection, XSS). This helps maintain the integrity of the system and prevents malicious code execution