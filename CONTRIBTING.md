# Contributing to AI Security Auditor

Thank you for your interest in contributing to the AI Security Auditor project! This document provides guidelines for contributing to the project.

## 🚀 Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/yourusername/ai-security-auditor.git
   cd ai-security-auditor
   ```
3. **Install dependencies**:
   ```bash
   npm install
   ```
4. **Set up environment variables** by copying `.env.example` to `.env` and filling in your values
5. **Set up the database**:
   ```bash
   npm run db:push
   ```

## 🛠️ Development Workflow

### Branch Naming
- Feature branches: `feature/description-of-feature`
- Bug fixes: `bugfix/description-of-bug`
- Documentation: `docs/description-of-change`

### Making Changes

1. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** following the code style guidelines below

3. **Test your changes**:
   ```bash
   npm run dev
   ```

4. **Commit your changes**:
   ```bash
   git add .
   git commit -m "feat: add description of your feature"
   ```

5. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

6. **Create a Pull Request** on GitHub

## 📝 Commit Message Guidelines

We use conventional commits for clear and consistent commit messages:

- `feat:` for new features
- `fix:` for bug fixes
- `docs:` for documentation changes
- `style:` for formatting changes
- `refactor:` for code refactoring
- `test:` for adding or updating tests
- `chore:` for maintenance tasks

Examples:
- `feat: add vulnerability severity filtering`
- `fix: resolve file upload error handling`
- `docs: update API documentation`

## 🎨 Code Style Guidelines

### TypeScript/JavaScript
- Use TypeScript for all new files
- Follow existing naming conventions
- Use meaningful variable and function names
- Add JSDoc comments for public functions
- Prefer arrow functions for callbacks
- Use destructuring where appropriate

### React Components
- Use functional components with hooks
- Follow the existing component structure in `client/src/components`
- Use TypeScript interfaces for props
- Implement proper error boundaries where needed

### Backend
- Use async/await instead of promises
- Implement proper error handling
- Add input validation using Zod schemas
- Follow RESTful API conventions

## 🧪 Testing

Currently, the project doesn't have automated tests, but we encourage:
- Manual testing of new features
- Testing across different browsers
- Verifying API endpoints work correctly
- Testing with various file types and code samples

## 📋 Areas for Contribution

### High Priority
- Add comprehensive test suite (Jest, React Testing Library)
- Implement user authentication and authorization
- Add more programming language support
- Improve error handling and user feedback
- Add vulnerability trend analysis over time

### Medium Priority
- Dark mode implementation
- Export reports as PDF/JSON
- Code syntax highlighting in vulnerability reports
- Batch file analysis
- Integration with popular IDEs

### Low Priority
- Real-time collaboration features
- API rate limiting
- Caching for analysis results
- Advanced filtering and search

## 🐛 Bug Reports

When reporting bugs, please include:
- Clear description of the issue
- Steps to reproduce
- Expected vs actual behavior
- Browser/OS information
- Console error messages (if any)
- Sample code that triggers the bug

## 💡 Feature Requests

For feature requests:
- Clearly describe the feature
- Explain the use case and benefits
- Consider implementation complexity
- Check if similar features already exist

## 📚 Documentation

Help improve documentation by:
- Fixing typos or unclear explanations
- Adding examples and use cases
- Updating API documentation
- Creating tutorials or guides

## 🔒 Security

If you discover security vulnerabilities:
- Do NOT open a public issue
- Email the maintainers directly
- Provide detailed information about the vulnerability
- Allow time for the issue to be addressed before disclosure

## 📞 Questions and Support

- Open an issue for bugs or feature requests
- Use GitHub Discussions for questions
- Check existing issues before creating new ones

## 📄 License

By contributing, you agree that your contributions will be licensed under the MIT License.

Thank you for contributing to AI Security Auditor!
