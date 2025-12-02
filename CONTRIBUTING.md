# Contributing to DropHub

🎉 **First off, thank you for considering contributing to DropHub!**

DropHub is a community-driven project, and we welcome contributions from everyone—whether you're fixing a typo, adding a feature, or building entire modules.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Recognition System](#recognition-system)

---

## 📜 Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md). 

**TL;DR**: Be respectful, inclusive, and constructive. We're building something amazing together.

---

## 🤝 How Can I Contribute?

### 1. **Report Bugs** 🐛
Found a bug? [Open an issue](https://github.com/YOUR_ORG/drophub/issues/new?template=bug_report.md) with:
- Clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Screenshots/logs (if applicable)
- Your environment (OS, PHP version, Node version)

### 2. **Suggest Features** 💡
Have an idea? [Open a feature request](https://github.com/YOUR_ORG/drophub/issues/new?template=feature_request.md) with:
- Clear description of the feature
- Why it's valuable to users
- Potential implementation approach
- Mockups/examples (if applicable)

### 3. **Write Code** 💻
Check out issues labeled:
- `good-first-issue` - Perfect for newcomers
- `help-wanted` - We need assistance here
- `hacktoberfest` - Great for Hacktoberfest participants

### 4. **Improve Documentation** 📖
- Fix typos or unclear explanations
- Add missing API documentation
- Create tutorials or video guides
- Translate documentation to other languages

### 5. **Design & UX** 🎨
- Improve UI/UX of WordPress plugin or admin dashboard
- Create marketing materials
- Design icons, logos, or illustrations

### 6. **Community Building** 🌍
- Answer questions on Discord
- Help triage GitHub issues
- Write blog posts about DropHub
- Speak at meetups/conferences

---

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed:
- **Git** 2.30+
- **Docker** 20.10+ & **Docker Compose** 2.0+
- **Node.js** 18 LTS or 20 LTS
- **PHP** 8.0+
- **Composer** 2.0+
- **Python** 3.9+ (for data sync tools)

### Setup Instructions

```bash
# 1. Fork the repository on GitHub
# Click "Fork" button at https://github.com/YOUR_ORG/drophub

# 2. Clone YOUR fork
git clone https://github.com/YOUR_USERNAME/drophub.git
cd drophub

# 3. Add upstream remote (to sync with main repo)
git remote add upstream https://github.com/YOUR_ORG/drophub.git

# 4. Copy environment template
cp .env.example .env

# 5. Edit .env with your local settings
nano .env

# 6. Start development environment
docker-compose up -d

# 7. Install dependencies
npm run install:all

# 8. Run database migrations
npm run migrate

# 9. Seed sample data (optional)
npm run seed

# 10. Verify everything is working
npm test
```

### Access Points

After setup, you can access:
- **API Server**: http://localhost:3000
- **API Documentation**: http://localhost:3000/api-docs
- **Admin Dashboard**: http://localhost:3001
- **WordPress Site**: http://localhost:8080
- **phpMyAdmin**: http://localhost:8081
- **Mailhog (Email Testing)**: http://localhost:8025

---

## 🔄 Development Workflow

### 1. Create a Feature Branch

```bash
# Always branch from main
git checkout main
git pull upstream main

# Create your feature branch
git checkout -b feature/amazing-feature
```

**Branch naming conventions:**
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation changes
- `refactor/` - Code refactoring
- `test/` - Adding tests
- `chore/` - Build process, dependencies

### 2. Make Your Changes

**For API changes:**
```bash
cd api-service
npm run dev  # Starts with hot-reload
```

**For WordPress plugin:**
```bash
cd wordpress-plugin
# Make changes and test in http://localhost:8080
```

**For Admin dashboard:**
```bash
cd admin-dashboard
npm start  # Starts React dev server
```

### 3. Test Your Changes

```bash
# Run unit tests
npm test

# Run linting
npm run lint

# Run type checking (if applicable)
npm run type-check

# Manual testing in browser
```

### 4. Commit Your Changes

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```bash
git add .
git commit -m "feat: add bulk product import"
```

**Commit types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Code formatting (no functional changes)
- `refactor:` - Code refactoring
- `test:` - Adding tests
- `chore:` - Build/dependency updates
- `perf:` - Performance improvements

**Examples:**
```bash
git commit -m "feat(api): add search suggestions endpoint"
git commit -m "fix(plugin): resolve image upload timeout"
git commit -m "docs: update API authentication guide"
```

### 5. Push and Create Pull Request

```bash
# Push to your fork
git push origin feature/amazing-feature

# Go to GitHub and create a Pull Request
# Target: YOUR_ORG/drophub:main ← YOUR_USERNAME/drophub:feature/amazing-feature
```

---

## 📏 Coding Standards

### JavaScript/Node.js

```javascript
// Use ESLint configuration
// Install: npm install

// Naming conventions
const CONSTANT_VALUE = 'value';  // Constants
const variableName = 'value';     // Variables
function functionName() {}        // Functions
class ClassName {}                // Classes

// Always use async/await (not .then())
async function getData() {
  const result = await fetchData();
  return result;
}

// Use destructuring
const { id, name } = product;

// Use template literals
const message = `Hello ${name}!`;
```

### PHP (WordPress Plugin)

```php
// Follow WordPress Coding Standards
// Use PHP_CodeSniffer with WordPress ruleset

// Naming conventions
const DROPHUB_VERSION = '0.1.0';  // Constants
$variable_name = 'value';         // Variables
function drophub_function_name()  // Functions
class DropHub_Class_Name {}       // Classes

// Escape output
echo esc_html($text);
echo esc_url($url);
echo esc_attr($attribute);

// Nonce verification
if (!wp_verify_nonce($nonce, 'action')) {
    wp_die('Security check failed');
}

// Database queries
$wpdb->prepare("SELECT * FROM table WHERE id = %d", $id);
```

### React (Admin Dashboard)

```javascript
// Use functional components with hooks
import React, { useState, useEffect } from 'react';

function ProductList() {
  const [products, setProducts] = useState([]);
  
  useEffect(() => {
    fetchProducts();
  }, []);
  
  return <div>{/* JSX */}</div>;
}

// Use prop types or TypeScript
import PropTypes from 'prop-types';

ProductCard.propTypes = {
  product: PropTypes.object.isRequired,
  onSelect: PropTypes.func.isRequired,
};
```

### SQL (Database)

```sql
-- Use snake_case for table/column names
CREATE TABLE products (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    sku VARCHAR(100) NOT NULL UNIQUE,
    title VARCHAR(255) NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    INDEX idx_sku (sku),
    INDEX idx_created_at (created_at)
);

-- Always use prepared statements in code
-- Never concatenate user input into queries
```

---

## 🎯 Pull Request Process

### Before Submitting

- ✅ Code follows project coding standards
- ✅ All tests pass (`npm test`)
- ✅ No linting errors (`npm run lint`)
- ✅ Documentation updated (if needed)
- ✅ Commit messages follow conventions
- ✅ Branch is up to date with main

### PR Title Format

```
<type>(<scope>): <description>

Examples:
feat(api): add product search endpoint
fix(plugin): resolve import button not working
docs(readme): add deployment instructions
```

### PR Description Template

```markdown
## Description
Brief description of what this PR does

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Related Issues
Closes #123
Relates to #456

## Testing
- [ ] Unit tests added/updated
- [ ] Manual testing completed
- [ ] Screenshots attached (for UI changes)

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] No new warnings generated
```

### Review Process

1. **Automated checks** run (tests, linting, build)
2. **Code review** by 1-2 maintainers
3. **Changes requested** (if needed)
4. **Approval** and **merge** by maintainer

**Average review time**: 2-5 days  
**For urgent fixes**: Tag with `priority: high`

---

## 🏆 Recognition System

### Contributor Levels

| Level | Requirements | Benefits |
|-------|-------------|----------|
| **🥉 First-Timer** | 1 merged PR | Welcome badge, Discord role |
| **🥈 Regular** | 5 merged PRs | Listed in CONTRIBUTORS.md |
| **🥇 Core** | 20 merged PRs | Name in README credits |
| **💎 Maintainer** | Invited by team | Write access, revenue share |

### Hall of Fame

Top contributors each quarter receive:
- 🎁 DropHub swag (stickers, t-shirts)
- 🎤 Feature on blog/social media
- 💰 Bounties for specific features (coming soon)

---

## 💬 Communication

### Discord Channels

Join our [Discord server](https://discord.gg/drophub):
- `#general` - General discussion
- `#development` - Technical discussions
- `#help` - Get help with setup/contributions
- `#api` - API development
- `#wordpress-plugin` - WordPress plugin
- `#admin-dashboard` - Admin dashboard (React)
- `#translations` - Localization help
- `#announcements` - Important updates

### GitHub Discussions

For longer-form discussions:
- [Feature Brainstorming](https://github.com/YOUR_ORG/drophub/discussions/categories/ideas)
- [Q&A](https://github.com/YOUR_ORG/drophub/discussions/categories/q-a)
- [Show and Tell](https://github.com/YOUR_ORG/drophub/discussions/categories/show-and-tell)

### Weekly Sync Calls

Every **Tuesday 3PM UTC** on Discord voice
- Review recent PRs
- Discuss upcoming features
- Community Q&A

---

## 📚 Resources

### Learning Materials
- [API Documentation](docs/API.md)
- [Architecture Overview](docs/ARCHITECTURE.md)
- [Database Schema](docs/DATABASE_SCHEMA.md)
- [Deployment Guide](docs/DEPLOYMENT.md)

### External Resources
- [WordPress Plugin Handbook](https://developer.wordpress.org/plugins/)
- [WooCommerce Docs](https://woocommerce.com/documentation/)
- [Express.js Guide](https://expressjs.com/en/guide/routing.html)
- [React Docs](https://react.dev/)

---

## ❓ Questions?

- 💬 Ask on [Discord](https://discord.gg/drophub)
- 📧 Email: contributors@drophub.org
- 🐦 Tweet [@DropHubProject](https://twitter.com/DropHubProject)

---

## 🙏 Thank You!

Every contribution, no matter how small, helps build a better DropHub.

**Together, we're revolutionizing e-commerce for everyone.** 🚀

---

<div align="center">

**[⬆ Back to Top](#contributing-to-drophub)**

**Made with ❤️ by the DropHub community**

</div>
