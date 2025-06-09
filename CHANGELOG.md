# Changelog

All notable changes to the AI Security Auditor project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-06-09

### Added
- Initial release of AI Security Auditor
- AI-powered code vulnerability analysis using GPT-3.5-turbo
- Support for multiple programming languages (JavaScript, TypeScript, Python, Java, PHP, C#, Ruby, Go, C++, C)
- File upload functionality with drag-and-drop interface
- Direct code input with syntax highlighting
- Customizable analysis options:
  - SQL Injection detection
  - Hardcoded secrets and API keys detection
  - Cross-Site Scripting (XSS) detection
  - Input validation issues detection
- Comprehensive security reports with:
  - Security score (0-10)
  - Vulnerability severity levels (Critical, Medium, Low)
  - Detailed descriptions and fix recommendations
  - Code examples and line numbers
- PostgreSQL database integration for persistent storage
- Real-time analysis statistics
- RESTful API with comprehensive endpoints
- Modern React frontend with Tailwind CSS
- Responsive design for mobile and desktop
- Error handling and user feedback

### Technical Features
- TypeScript throughout the entire codebase
- Drizzle ORM for type-safe database operations
- TanStack Query for efficient data fetching
- Zod schemas for runtime validation
- Express.js backend with proper middleware
- File upload validation and security
- Environment-based configuration
- Comprehensive error handling

### Documentation
- Complete README with setup instructions
- API documentation with examples
- Contributing guidelines
- Deployment guide
- License (MIT)

### Security
- Input validation on all endpoints
- File type and size restrictions
- Secure environment variable handling
- SQL injection prevention through parameterized queries
- XSS protection through proper data sanitization

## [Unreleased]

### Planned Features
- User authentication and authorization
- Analysis history and trending
- Export reports to PDF/JSON
- Dark mode support
- Batch file analysis
- Real-time collaboration
- IDE integrations
- Custom vulnerability rules
- API rate limiting
- Advanced filtering and search
