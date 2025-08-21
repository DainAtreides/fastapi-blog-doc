# FastAPI Blog Platform

## About the Project
This is a fully functional, production-ready web application focused on clean backend architecture, robust security, and a responsive, handcrafted frontend experience.

The backend is developed using FastAPI, with modular routing, asynchronous SQLAlchemy integration, and PostgreSQL as the database. It supports user authentication, role-based access control, and full CRUD operations, with passwords securely hashed following best practices.

To ensure content safety, the application integrates the Sightengine API for automatic detection and filtering of NSFW images uploaded as avatars.

The frontend avoids heavy frameworks, relying on custom JavaScript for dynamic UI elements like modals, forms, and a rich-text editor powered by a customized TipTap implementation, featuring a bespoke toolbar, placeholder support, and real-time empty content detection.

Styling is implemented with modular SCSS, designed for maintainability, clarity, and responsiveness across devices.

Overall, this project demonstrates the creation of a scalable, secure, and user-friendly web application built from the ground up, emphasizing simplicity and effectiveness over boilerplate or overengineering.

## Demo

🟢 Live demo: [https://mono-core.ru](https://mono-core.ru)

## Features

### Secure and Scalable Backend
- Built with FastAPI and asynchronous SQLAlchemy.  
- Modular codebase with separated routers, models, schemas, and CRUD logic.  
- Session-based authentication managed via SessionMiddleware.  
- Passwords securely hashed using bcrypt.  
- Custom exception handling and application lifespan lifecycle hooks.

### Rich Text Editing and Dynamic Forms
- Powerful TipTap editor with custom toolbar and placeholder support.  
- Real-time detection of empty content with dynamic UI feedback.  
- Modal dialogs and dynamic forms implemented in clean vanilla JavaScript.

### Maintainable and Scalable Styling
- Organized SCSS architecture with variables, mixins, and grid layouts.  
- Reusable components with semantic class naming conventions.  
- Easy theming and extensibility as the project evolves.

### Safe Media Uploads
- Avatar uploads scanned for NSFW content via Sightengine API.  
- Fallback to default avatars when inappropriate content detected.  
- Robust file validation and custom error handling for upload failures.

## Tech Stack

- **FastAPI** — modern, high-performance web framework with asynchronous support for building APIs.
- **Async SQLAlchemy** — asynchronous ORM for clean and efficient interaction with PostgreSQL.
- **PostgreSQL** — reliable, scalable relational database for structured data storage.
- **Pydantic** — data validation and serialization for requests and responses.
- **Jinja2 Templates** — server-side rendering of HTML pages with templating.
- **Passlib (bcrypt)** — secure password hashing and verification.
- **Session Middleware** — session management handling authentication and authorization.
- **Sightengine API** — automatic content moderation for user-uploaded avatars, filtering NSFW images.

## Project Structure
```graphql
root/
├── alembic/                      # Alembic migrations
├── app/
│   ├── crud/                     # Async DB access logic (users, posts, comments)
│   ├── routers/                  # All route definitions, separated by domain
│   ├── static/                   # Static files (styles, JS, images, icons)
│   ├── templates/                # Jinja2 templates
│   ├── admin_setup.py            # Initial admin creation logic
│   ├── auth.py                   # Authentication helpers
│   ├── config.py                 # App configuration
│   ├── database.py               # DB engine/session setup
│   ├── init_db.py                # DB table initialization
│   ├── main.py                   # FastAPI entry point
│   ├── models.py                 # SQLAlchemy models
│   └── schemas.py                # Pydantic schemas
├── .env                          # Environment variables
├── Dockerfile                    # App Docker build
├── Dockerfile.sass               # Sass-to-CSS build image
├── docker-compose.yml            # Compose config for app & db
├── requirements.txt              # Dependencies
└── alembic.ini                   # Alembic config
```

## Security Notes

- **Password Hashing:**  
  User passwords are never stored in plain text. The project uses `passlib` with the `bcrypt` algorithm to securely hash passwords during user creation and password updates.
- **Password Verification:**  
  Passwords are verified using a secure hash comparison function to prevent any exposure of plaintext passwords during authentication and password changes.
- **User Uniqueness Enforcement:**  
  The system ensures uniqueness of email, username, and nickname on user registration and profile updates to prevent conflicts and impersonation risks.
- **Avatar File Management:**  
  When a user updates their avatar, the old non-default avatar file is deleted from the server filesystem, preventing accumulation of obsolete files and potential misuse.
- **Data Integrity and Access Control:**  
  User update operations strictly validate input fields and ensure changes are applied only to the intended user, preventing unauthorized data modification.
- **Error Handling:**  
  All critical operations raise precise HTTP exceptions with appropriate status codes and clear error messages, avoiding information leakage while supporting debugging.
- **Session Management and Authentication:**  
  User sessions and authentication state are handled via dedicated middleware (`SessionMiddleware`), ensuring robust session security and protected access to restricted endpoints.
- **Role-Based Access Control (RBAC):**  
  User roles (e.g., `admin`) are enforced in queries and route access, enabling fine-grained permission control and enhancing overall application security.

## Future Plans

1. **Expand User Models**  
   - Implement friend relationships and follower/subscription systems to foster user interaction.  
   - Introduce new entities such as tags and categories to organize posts better and enable content filtering.
2. **Thematic Sections**  
   - Add support for thematic or topic-based sections, allowing users to browse and contribute to focused content areas.
3. **Post and Comment Rating System**  
   - Implement upvote/downvote or like/dislike mechanics for posts and comments to encourage quality content.
4. **Sorting and Filtering by Rating**  
   - Enable sorting posts and comments by their rating scores, improving content discovery and user engagement.
5. **User Profile Reputation**  
   - Calculate and display an aggregate reputation score or ranking for user profiles based on activity, ratings, and contributions.
6. **Notification System**  
   - Introduce real-time notifications for user interactions such as new comments, likes, friend requests, or messages.
7. **Advanced Search and Filtering**  
   - Develop a powerful search engine supporting full-text search, tag filtering, date ranges, and user-specific queries.
8. **API Versioning and Documentation**  
   - Enhance API stability and developer experience by implementing versioning and expanding automated documentation.
9. **Localization and Internationalization**  
   - Prepare the platform to support multiple languages and regional settings for a broader audience.
10. **Performance Optimization and Caching**  
    - Introduce caching layers, query optimizations, and CDN integration to improve response times and scalability.
11. **Mobile-Friendly Enhancements**  
    - Improve frontend responsiveness and UX tailored for mobile and tablet devices.
12. **Security Enhancements**  
    - Implement features like two-factor authentication (2FA), account recovery options, and stricter rate limiting.

## Notes

- Project is closed-source, deployed on a private VPS.
- Demo is fully functional and available 24/7.
- Developed for portfolio purposes.
