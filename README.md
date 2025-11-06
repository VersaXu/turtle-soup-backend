# 🐢 Turtle Soup Backend API

![Backend Service](https://img.shields.io/badge/Backend-API_Service-blue)
![Node.js](https://img.shields.io/badge/Node.js-Express-green)
![Vercel](https://img.shields.io/badge/Deployment-Vercel-black)

## Project Overview

This is the backend API service for the Turtle Soup puzzle game, providing question answering, puzzle generation, and user authentication functionality for the frontend game. The service is built with Express.js and deployed on Vercel platform.

### API Service

URL: https://turtle-soup-backend-hsry.vercel.app/

## Features

- Integration with Qwen API for intelligent question answering
- Puzzle generation and management
- User authentication (simplified version)
- CORS configuration for frontend cross-domain requests
- Serverless deployment on Vercel

## Technical Architecture

- **Backend Framework**: Express.js
- **Runtime**: Node.js
- **API Integration**: Alibaba Cloud Qwen
- **Deployment Platform**: Vercel
- **Frontend Communication**: CORS support

## API Endpoints

### Health Check
- `GET /` - Returns service status information

### Chat API
- `POST /api/qwen/chat` - Interact with Qwen model
  - Request body: `{ "prompt": "User input question" }`
  - Response: `{ "result": "AI response content" }`

### Authentication API
- `POST /api/auth/login` - User login
  - Request body: `{ "username": "username", "password": "password" }`
  - Response: User information with access token

- `POST /api/auth/register` - User registration
  - Request body: `{ "username": "username", "password": "password" }`
  - Response: User information with access token

## Local Development

### Prerequisites

- Node.js 14.x or higher
- npm or yarn
- Qwen API key (optional)

### Installation Steps

1. Clone repository
```bash
git clone https://github.com/VersaXu/turtle-soup-backend.git
cd turtle-soup-backend
```

2. Install dependencies
```bash
npm install
# or
yarn install
```

3. Create environment variables file
```bash
echo "QWEN_API_KEY=your_api_key_here" > .env
```

4. Start development server
```bash
npm start
# or
yarn start
```

The service will run at http://localhost:3000.

## Project Structure

```
/
├── turtle-soup-server.js  # Main server file
├── package.json          # Project dependencies
├── vercel.json           # Vercel deployment configuration
└── .env                  # Environment variables (for local development)
```

## Deployment

The project is configured for automatic deployment on Vercel. When code is pushed to the main branch, Vercel automatically builds and deploys a new version.

### Deployment Steps

1. Create a new project on Vercel
2. Connect GitHub repository
3. Configure environment variables:
   - `QWEN_API_KEY`: Qwen API key
   - `QWEN_BASE_URL`: API base URL (optional)
   - `QWEN_MODEL`: Model to use (optional)
4. Deploy the project

## Configuration

### Environment Variables

- `QWEN_API_KEY`: Qwen API key
- `QWEN_BASE_URL`: Qwen API base URL
- `QWEN_MODEL`: Model name to use
- `PORT`: Local development server port

### Vercel Configuration

The vercel.json file contains the configuration needed for Vercel deployment:

```json
{
  "version": 2,
  "builds": [
    {
      "src": "turtle-soup-server.js",
      "use": "@vercel/node"
    }
  ],
  "rewrites": [
    { "source": "/api/(.*)", "destination": "/turtle-soup-server.js" }
  ]
}
```

## Frontend Integration

The frontend project configures the API address through environment variables:

```
VITE_API_BASE_URL=https://turtle-soup-backend-hsry.vercel.app/api
```

## Contributing

Welcome to contribute to the project! You can participate through:

1. Submitting issues or suggestions
2. Contributing code improvements
3. Enhancing AI answering capabilities

## License

[MIT](LICENSE)

## Acknowledgments

- Alibaba Cloud Qwen team
- Express.js community
- Vercel platform
- Project contributors