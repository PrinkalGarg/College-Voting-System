# College Voting System Backend

This is the backend server for the College Voting System. It provides RESTful APIs for managing elections, candidates, and voters.

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (v4.4 or higher)
- npm or yarn

## Setup

1. Install dependencies:
```bash
npm install
```

2. Create a `.env` file in the root directory with the following variables:
```
PORT=5000
MONGODB_URI=your mongodb connectivity
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
```

3. Start MongoDB:
```bash
mongod
```

4. Start the server:
```bash
# Development mode with nodemon
npm run dev

# Production mode
npm start
```

## API Endpoints

### Elections
- GET /api/elections - Get all elections
- GET /api/elections/:id - Get single election
- POST /api/elections - Create election (admin only)
- PUT /api/elections/:id - Update election (admin only)
- DELETE /api/elections/:id - Delete election (admin only)
- POST /api/elections/:id/vote - Vote in an election (authenticated users)

### Candidates
- GET /api/candidates - Get all candidates
- GET /api/candidates/election/:electionId - Get candidates for an election
- GET /api/candidates/:id - Get single candidate
- POST /api/candidates - Create candidate (admin only)
- PUT /api/candidates/:id - Update candidate (admin only)
- DELETE /api/candidates/:id - Delete candidate (admin only)
- POST /api/candidates/:id/vote - Vote for a candidate (authenticated users)

### Voters
- POST /api/voters/register - Register new voter
- POST /api/voters/login - Login voter
- GET /api/voters - Get all voters (admin only)
- GET /api/voters/:id - Get single voter (admin only)
- PUT /api/voters/:id - Update voter profile
- DELETE /api/voters/:id - Delete voter (admin only)
- GET /api/voters/:id/voted-elections - Get voter's voted elections

## Authentication

The API uses JWT (JSON Web Tokens) for authentication. Include the token in the Authorization header:
```
Authorization: Bearer <your-token>
```

## Error Handling

The API returns appropriate HTTP status codes and error messages in the following format:
```json
{
  "message": "Error message here"
}
```

## Security

- Passwords are hashed using bcrypt
- JWT tokens expire after 24 hours
- Admin routes are protected
- Input validation is performed on all routes 