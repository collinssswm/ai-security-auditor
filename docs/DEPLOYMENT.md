# Deployment Guide

This guide covers different deployment options for the AI Security Auditor application.

## Quick Deploy Options

### Replit Deployment
1. Fork this repository on GitHub
2. Import to Replit
3. Set environment variables in Replit Secrets
4. Click "Deploy" in Replit

### Vercel (Frontend + Serverless Functions)
1. Fork the repository
2. Connect to Vercel
3. Configure environment variables
4. Deploy with automatic builds

### Railway (Full-Stack)
1. Connect GitHub repository to Railway
2. Add PostgreSQL database service
3. Configure environment variables
4. Deploy with automatic builds

## Manual Deployment

### Prerequisites
- Node.js 18+
- PostgreSQL database
- OpenAI API key

### Environment Variables
```bash
DATABASE_URL=postgresql://user:password@host:port/database
OPENAI_API_KEY=sk-your-openai-api-key
PORT=5000
NODE_ENV=production
```

### Build and Deploy
```bash
# Install dependencies
npm install

# Build the application
npm run build

# Set up database
npm run db:push

# Start production server
npm start
```

## Docker Deployment

### Create Dockerfile
```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production

COPY . .
RUN npm run build

EXPOSE 5000

CMD ["npm", "start"]
```

### Docker Compose
```yaml
version: '3.8'
services:
  app:
    build: .
    ports:
      - "5000:5000"
    environment:
      - DATABASE_URL=postgresql://postgres:password@db:5432/ai_security_auditor
      - OPENAI_API_KEY=your-api-key
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      - POSTGRES_DB=ai_security_auditor
      - POSTGRES_PASSWORD=password
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

## Cloud Provider Specific Guides

### AWS
1. Use AWS RDS for PostgreSQL
2. Deploy on AWS ECS or Elastic Beanstalk
3. Configure environment variables in AWS Systems Manager

### Google Cloud
1. Use Cloud SQL for PostgreSQL
2. Deploy on Google Cloud Run
3. Set environment variables in Cloud Run configuration

### Azure
1. Use Azure Database for PostgreSQL
2. Deploy on Azure Container Instances
3. Configure environment variables in Azure portal

## Performance Optimization

### Production Recommendations
- Enable gzip compression
- Implement caching for static assets
- Use CDN for file uploads
- Monitor OpenAI API usage
- Set up health checks

### Scaling Considerations
- Implement rate limiting
- Add Redis for session storage
- Use load balancers for multiple instances
- Monitor database performance

## Security Checklist

### Before Deployment
- [ ] All secrets stored securely
- [ ] HTTPS enabled
- [ ] Database connections encrypted
- [ ] Input validation implemented
- [ ] Error handling doesn't expose sensitive data
- [ ] CORS configured appropriately
- [ ] File upload limits enforced

### Post-Deployment
- [ ] Monitor error logs
- [ ] Set up alerts for API failures
- [ ] Regular security updates
- [ ] Database backups configured
- [ ] Performance monitoring enabled
