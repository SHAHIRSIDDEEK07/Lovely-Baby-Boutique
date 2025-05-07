# Lovely-Baby-Boutique
for shopify
name: Storefront 1000035412

on: [push]

permissions:
  contents: read
  deployments: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18' # Use the latest LTS version for better compatibility

      - name: Install dependencies
        run: npm ci

      - name: Build project
        run: npm run build # Replace with a specific build command if applicable

      - name: Deploy to Oxygen
        run: npx shopify hydrogen deploy
        env:
          SHOPIFY_HYDROGEN_DEPLOYMENT_TOKEN: ${{ secrets.OXYGEN_DEPLOYMENT_TOKEN_1000035412 }}
