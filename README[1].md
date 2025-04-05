# Pi Network Payment Backend

This is a simple backend server for handling Pi Network payments for your RetroArcade games hosted on GitHub Pages.

## Setup Instructions

1. Clone this repository
2. Install dependencies: `npm install`
3. Create a `.env` file based on `.env.example`
4. Start the server: `npm start`

## Environment Variables

- `PI_API_KEY`: Your Pi API Key from the Developer Portal
- `PI_CLIENT_SECRET`: Your Pi Client Secret from the Developer Portal
- `FRONTEND_URL`: Your frontend URL (GitHub Pages URL)
- `PORT`: Port for the server to run on
- `SANDBOX_MODE`: Set to 'true' for testing, 'false' for production

## API Endpoints

- `GET /`: Health check endpoint
- `POST /api/payments/approve`: Approves Pi payments
- `POST /api/payments/complete`: Completes Pi payments
- `POST /api/payments/webhook`: Handles Pi Network webhooks

## Deployment

This server can be deployed to Render or any other Node.js hosting service.

## Frontend Integration

Update your frontend code to point to this backend server for payment processing.
