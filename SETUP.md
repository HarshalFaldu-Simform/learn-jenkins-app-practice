# Setup Guide for Learn Jenkins App

This guide will help you clone and set up this repository for your own use.

## Prerequisites

- Node.js 18 or higher
- npm (comes with Node.js)
- Docker (for Jenkins pipeline and AWS CLI operations)
- AWS Account (for deployment)
- Jenkins server (for CI/CD)

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/learn-jenkins-app-practice.git
cd learn-jenkins-app-practice
```

### 2. Install Dependencies

```bash
npm ci
```

### 3. Run the Application Locally

```bash
npm start
```

The app will open at [http://localhost:3000](http://localhost:3000)

### 4. Build the Application

```bash
npm run build
```

### 5. Run Tests

```bash
npm test
```

## Configuration for Your Environment

### AWS Configuration

The repository includes Jenkins pipeline configurations for AWS deployment. You'll need to update the following files with your AWS account details:

#### 1. Update Jenkinsfile

Edit `Jenkinsfile` and update these environment variables:

```groovy
environment {
    REACT_APP_VERSION  = "1.0.$BUILD_ID"
    APP_NAME = 'learnjenkinsapp'  // Change to your app name
    AWS_DEFAULT_REGION = 'us-east-1'  // Change to your AWS region
    AWS_DOCKER_REGISTRY = 'YOUR-AWS-ACCOUNT-ID.dkr.ecr.us-east-1.amazonaws.com'  // Update with your ECR registry
    AWS_ECS_CLUSTER = 'your-ecs-cluster-name'  // Update with your ECS cluster name
    AWS_ECS_SERVICE = 'your-ecs-service-name'  // Update with your ECS service name
    AWS_ECS_TD_PROD = 'your-task-definition-name'  // Update with your task definition name
}
```

#### 2. Update AWS Task Definition

Edit `aws/task-definition-prod.json` and update:

- `family`: Your task definition family name
- `image`: Your ECR repository URL
- `executionRoleArn`: Your AWS IAM role ARN

Example:
```json
{
    "family": "YourApp-TaskDefinition-Prod",
    "containerDefinitions": [{
        "image": "YOUR-AWS-ACCOUNT-ID.dkr.ecr.us-east-1.amazonaws.com/yourapp:#APP_VERSION#",
        // ... other settings
    }],
    "executionRoleArn": "arn:aws:iam::YOUR-AWS-ACCOUNT-ID:role/ecsTaskExecutionRole"
}
```

### Jenkins Configuration

1. **AWS Credentials**: In Jenkins, create credentials with ID `my-aws` containing your AWS access key and secret key
2. **Docker**: Ensure Jenkins has Docker installed and configured
3. **AWS CLI Image**: Build the `my-aws-cli` Docker image referenced in the Jenkinsfile, or replace it with an appropriate AWS CLI image

### Creating Your Own AWS Resources

Before deploying, you need to create:

1. **ECR Repository**: 
   ```bash
   aws ecr create-repository --repository-name yourapp --region us-east-1
   ```

2. **ECS Cluster**:
   ```bash
   aws ecs create-cluster --cluster-name your-cluster-name --region us-east-1
   ```

3. **ECS Service and Task Definition**: Use the AWS Console or CLI to create your service based on the task definition template

4. **IAM Role**: Ensure you have an ECS task execution role with appropriate permissions

## Project Structure

```
.
├── src/                  # React application source code
├── public/              # Static public assets
├── aws/                 # AWS configuration files
│   └── task-definition-prod.json
├── Jenkinsfile         # Main Jenkins pipeline
├── Jenkinsfile-nightly # Nightly build pipeline
├── Dockerfile          # Container configuration
├── package.json        # Node.js dependencies
└── README.md           # Basic documentation
```

## Available Scripts

- `npm start` - Run development server
- `npm test` - Run tests
- `npm run build` - Create production build
- `npm run eject` - Eject from Create React App (one-way operation)

## Troubleshooting

### Issue: AWS deployment fails
- Verify all AWS resource names in Jenkinsfile match your actual resources
- Check Jenkins has valid AWS credentials configured
- Ensure your AWS IAM user/role has necessary permissions for ECS, ECR operations

### Issue: Docker build fails in Jenkins
- Verify Docker is installed and running on Jenkins agent
- Check Docker socket is accessible: `/var/run/docker.sock`

### Issue: Tests fail
- Run `npm ci` to ensure dependencies are correctly installed
- Check Node.js version matches project requirements (18+)

## Contributing

When making changes:
1. Create a feature branch
2. Make your changes
3. Run tests: `npm test`
4. Build the app: `npm run build`
5. Commit and push your changes

## License

This is a learning project for Jenkins CI/CD practices.
