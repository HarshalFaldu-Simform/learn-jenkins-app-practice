# Quick Start Guide

Get up and running with this repository in 5 minutes!

## For Local Development Only

If you just want to run the app locally without Jenkins or AWS:

```bash
# 1. Clone the repository
git clone https://github.com/YOUR-USERNAME/learn-jenkins-app-practice.git
cd learn-jenkins-app-practice

# 2. Install dependencies
npm ci

# 3. Start the development server
npm start
```

That's it! The app will open at http://localhost:3000

## For Full CI/CD Setup

If you want to set up the complete Jenkins pipeline with AWS deployment:

1. **Read the detailed guide**: [SETUP.md](SETUP.md)
2. **Create AWS resources**: ECR repository, ECS cluster, service, and task definition
3. **Configure Jenkins**: Set up credentials and install Docker
4. **Customize configuration files**:
   - Copy `Jenkinsfile.template` to `Jenkinsfile` and update values
   - Copy `aws/task-definition-prod.json.template` and customize
5. **Run your pipeline**: Push changes to trigger Jenkins build

## Quick Commands Reference

```bash
npm ci              # Install dependencies (clean install)
npm start           # Run development server (localhost:3000)
npm test            # Run tests
npm run build       # Build for production
npm run eject       # Eject from Create React App (irreversible)
```

## Need Help?

- 📖 **Detailed Setup**: See [SETUP.md](SETUP.md)
- 🤝 **Contributing**: See [CONTRIBUTING.md](CONTRIBUTING.md)
- 📝 **Basic Info**: See [README.md](README.md)

## Common Issues

**Issue**: `npm ci` fails
- **Solution**: Ensure you have Node.js 18+ installed

**Issue**: Port 3000 already in use
- **Solution**: Stop other apps using port 3000, or set `PORT=3001 npm start`

**Issue**: Tests fail
- **Solution**: Run `npm ci` again to ensure clean install

---

💡 **Tip**: For quick experiments, you don't need to set up AWS or Jenkins - just use `npm start` for local development!
