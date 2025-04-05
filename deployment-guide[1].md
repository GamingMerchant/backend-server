# Pi Network Integration Deployment Guide

This guide provides step-by-step instructions for deploying your Pi Network payment integration for your RetroArcade games.

## 1. Backend Server Deployment (Render)

### Step 1: Create a GitHub Repository
1. Create a new GitHub repository for your backend server
2. Upload all files from the `pi-payments-backend` folder (excluding the `frontend` folder)
3. Make sure to include `.gitignore` and add `.env` to it

### Step 2: Deploy to Render
1. Sign up for a Render account at [render.com](https://render.com)
2. From your dashboard, click "New" and select "Web Service"
3. Connect your GitHub repository
4. Configure the service:
   - Name: `pi-payments-backend`
   - Environment: `Node`
   - Build Command: `npm install`
   - Start Command: `node server.js`
5. Add environment variables:
   - `PI_API_KEY`: Your Pi API Key from the Developer Portal
   - `PI_CLIENT_SECRET`: Your Pi Client Secret from the Developer Portal
   - `FRONTEND_URL`: `https://gamingmerchant.github.io/Gamechanger`
   - `PORT`: `3000`
   - `SANDBOX_MODE`: `true` (change to `false` for production)
6. Click "Create Web Service"
7. Wait for the deployment to complete
8. Note your service URL (e.g., `https://pi-payments-backend.onrender.com`)

## 2. Frontend Integration

### Step 1: Update Frontend Code
1. Copy `pi-payments.js` from the `frontend` folder to your GitHub Pages repository
2. Place it in the `js` folder of your RetroArcade project
3. Update the `BACKEND_URL` in `pi-payments.js` to your Render service URL
4. Update the `apiKey` in the Pi.init() call with your actual API key

### Step 2: Include the Script in Your HTML Files
Add the following to the head section of each game HTML file:
```html
<script src="https://sdk.minepi.com/pi-sdk.js"></script>
<script src="js/pi-payments.js"></script>
```

### Step 3: Update Button Event Listeners
Update your payment buttons to call the appropriate functions:
```html
<button id="buy-extra-lives" class="pi-button">BUY 3 EXTRA LIVES (π 1.00)</button>
<script>
  document.getElementById('buy-extra-lives').addEventListener('click', buyExtraLives);
</script>
```

## 3. Privacy Policy Setup

### Step 1: Customize the Privacy Policy
1. Copy `privacy-policy.html` from the `frontend` folder to your GitHub Pages repository
2. Update the following information:
   - Your email address in the "Contact Us" section
   - Your website URL
   - The "Last Updated" date if needed
   - Any specific details about your data collection practices

### Step 2: Upload to GitHub Pages
1. Add the privacy policy to your GitHub repository
2. Commit and push the changes
3. The privacy policy will be available at `https://gamingmerchant.github.io/Gamechanger/privacy-policy.html`

### Step 3: Add to Pi Developer Portal
1. Log in to the [Pi Developer Portal](https://developers.minepi.com)
2. Go to your app settings
3. In the "Privacy Policy URL" field, enter `https://gamingmerchant.github.io/Gamechanger/privacy-policy.html`
4. Save your changes

## 4. Pi Developer Portal Configuration

### Step 1: Register Your App
1. Log in to the [Pi Developer Portal](https://developers.minepi.com)
2. Click "Create New App"
3. Fill in the required information:
   - App Name: "RetroArcade"
   - App Description: Brief description of your retro games platform
   - Category: "Games"
   - Website URL: `https://gamingmerchant.github.io/Gamechanger`
4. For Platform, select "Web"
5. Add redirect URLs: `https://gamingmerchant.github.io/Gamechanger`
6. Add your Privacy Policy URL: `https://gamingmerchant.github.io/Gamechanger/privacy-policy.html`
7. Save your app

### Step 2: Configure Webhooks
1. In your app settings, go to the "Webhooks" section
2. Add your backend webhook URL: `https://pi-payments-backend.onrender.com/api/payments/webhook`
3. Save your changes

## 5. Testing

### Step 1: Test in Pi Browser
1. Install the Pi Browser on your mobile device
2. Open your GitHub Pages URL: `https://gamingmerchant.github.io/Gamechanger`
3. Test the authentication flow by clicking on a payment button
4. Verify that you can authenticate with Pi Network
5. Test a payment transaction
6. Check your backend logs on Render to verify webhook calls

### Step 2: Verify Premium Features
1. After a successful payment, verify that premium features are unlocked
2. Test each game to ensure premium features work correctly
3. Verify that premium status is saved between sessions

## 6. Going to Production

### Step 1: Apply for Production Access
1. In the Pi Developer Portal, request production access
2. Complete the required information and submit for review
3. Wait for approval from the Pi Network team

### Step 2: Update Configuration
1. Update your backend environment variables:
   - Set `SANDBOX_MODE` to `false`
2. Update your frontend code:
   - Set `sandbox: false` in the Pi.init() call

### Step 3: Final Testing
1. Test the complete flow in production environment
2. Verify all features work as expected

## Troubleshooting

- **Payment Approval Fails**: Check your PI_API_KEY and PI_CLIENT_SECRET
- **Webhook Not Received**: Verify your webhook URL in the Pi Developer Portal
- **CORS Errors**: Ensure your backend CORS configuration allows your frontend URL
- **Authentication Issues**: Check your API key and sandbox mode settings
