# Contributing to OmniFocus MCP

Thank you for your interest in contributing to OmniFocus MCP! This guide will help you get started.

## 🚀 Getting Started

1. Fork the repository
2. Clone your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/OmniFocus-MCP.git
   cd OmniFocus-MCP
   ```
3. Install dependencies:
   ```bash
   npm install
   ```
4. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## 🧪 Development Workflow

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage
```

### Building the Project

```bash
npm run build
```

### Testing Locally

To test your changes with Claude Desktop:

1. Build the project: `npm run build`
2. Update your Claude Desktop config to point to your local build:
   ```json
   {
     "mcpServers": {
       "omnifocus": {
         "command": "node",
         "args": ["/path/to/your/local/OmniFocus-MCP/cli.cjs"]
       }
     }
   }
   ```

## ✅ Pull Request Process

### Before Submitting

1. **Ensure all tests pass**: Run `npm test`
2. **Add tests for new features**: Source changes require corresponding test changes
3. **Update documentation**: Update README.md if you've added new features
4. **Check TypeScript**: Run `npx tsc --noEmit` to ensure no type errors
5. **Follow code style**: Match the existing code style in the project

### CI/CD Checks

When you submit a PR, the following automated checks will run:

1. **Test Suite**: Tests run on macOS with Node.js 18.x and 20.x
2. **TypeScript Compilation**: Ensures the project builds without errors
3. **Test Coverage**: Checks that code coverage meets minimum thresholds (70%)
4. **Security Audit**: Scans for known vulnerabilities
5. **Bundle Size**: Ensures the distribution size stays under 10MB

### PR Requirements

- PRs that modify source files (`src/**/*.ts`) must include test changes
- All CI checks must pass before merging
- Code coverage must remain above 70%
- No high or critical security vulnerabilities

## 🏗️ Project Structure

```
OmniFocus-MCP/
├── src/
│   ├── tools/
│   │   ├── definitions/    # Tool schemas and handlers
│   │   └── primitives/     # Core logic and AppleScript
│   ├── utils/
│   │   └── omnifocusScripts/  # JXA/AppleScript files
│   ├── types.ts           # TypeScript interfaces
│   └── server.ts          # MCP server entry point
├── src/__tests__/         # Test files
└── dist/                  # Built output
```

## 🧪 Writing Tests

Tests use Jest with ESM support. Follow these patterns:

```typescript
import { describe, it, expect, jest } from '@jest/globals';

// Mock dependencies before imports
const mockFunction = jest.fn();
jest.unstable_mockModule('../module.js', () => ({
  functionName: mockFunction
}));

// Import after mocking
const { myFunction } = await import('../myFunction.js');

describe('myFunction', () => {
  it('should do something', async () => {
    // Test implementation
  });
});
```

## 📝 Commit Messages

Follow conventional commit format:

- `feat:` New features
- `fix:` Bug fixes
- `docs:` Documentation changes
- `test:` Test additions or changes
- `chore:` Maintenance tasks
- `refactor:` Code refactoring

Example: `feat: add support for nested tasks`

## 🚀 Release Process

Releases are automated when the version in `package.json` is bumped on the main branch:

1. Update version in `package.json`
2. Commit and push to main
3. CI/CD will automatically:
   - Run all tests
   - Publish to npm
   - Create a GitHub release

## 💬 Getting Help

- Open an issue for bugs or feature requests
- Use discussions for general questions
- Check existing issues before creating new ones

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.