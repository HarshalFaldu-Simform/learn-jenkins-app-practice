# Contributing to Learn Jenkins App

Thank you for your interest in contributing to this project! This guide will help you get started.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/learn-jenkins-app-practice.git
   cd learn-jenkins-app-practice
   ```
3. **Add the upstream repository**:
   ```bash
   git remote add upstream https://github.com/ORIGINAL-OWNER/learn-jenkins-app-practice.git
   ```

## Setting Up Your Development Environment

1. Install dependencies:
   ```bash
   npm ci
   ```

2. Run the development server:
   ```bash
   npm start
   ```

3. The app should open at http://localhost:3000

## Making Changes

1. **Create a new branch** for your feature or fix:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** following these guidelines:
   - Write clear, readable code
   - Follow the existing code style
   - Add comments for complex logic
   - Keep changes focused and minimal

3. **Test your changes**:
   ```bash
   npm test
   ```

4. **Build the app** to ensure it compiles:
   ```bash
   npm run build
   ```

## Commit Guidelines

- Write clear, descriptive commit messages
- Use present tense ("Add feature" not "Added feature")
- Reference issues in commits when applicable (#123)
- Keep commits atomic (one logical change per commit)

Example:
```
Add user authentication feature

- Implement login form component
- Add authentication API integration
- Update routing for protected pages

Fixes #123
```

## Pull Request Process

1. **Update your branch** with the latest changes from upstream:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Push your changes** to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```

3. **Create a Pull Request** on GitHub with:
   - Clear title describing the change
   - Detailed description of what was changed and why
   - Reference to any related issues
   - Screenshots for UI changes

4. **Wait for review** and address any feedback

## Code Style

This project uses:
- React best practices
- ESLint for code linting (configured in package.json)
- Functional components with hooks

## Testing

- Write tests for new features
- Ensure all tests pass before submitting PR
- Tests are run with Jest and React Testing Library

Run tests:
```bash
npm test
```

## Documentation

- Update README.md if you change functionality
- Update SETUP.md if you change configuration or setup steps
- Add JSDoc comments for complex functions
- Update this guide if you change the contribution process

## Questions or Problems?

- Open an issue on GitHub
- Clearly describe the problem or question
- Include relevant code snippets or error messages
- Mention your environment (OS, Node version, etc.)

## License

By contributing, you agree that your contributions will be licensed under the same license as the project.

Thank you for contributing! 🎉
