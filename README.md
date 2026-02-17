# Bundle & Save

## Project Overview
- **Name**: Bundle & Save
- **Goal**: E-commerce product bundling interface with dynamic pricing and discount tiers
- **Features**: 
  - Interactive bundle selection (1, 2, or 3 pair bundles)
  - Dynamic pricing calculation based on bundle selection
  - Size and color selection for individual items
  - Real-time total price updates
  - Responsive design with Tailwind CSS
  - Custom styled radio buttons and dropdowns

## URLs
- **Development**: https://3000-idjcuaa4m9o5e1fqkxorf-ad490db5.sandbox.novita.ai
- **GitHub**: (Not yet deployed)

## Currently Completed Features
1. ✅ Three bundle tiers with progressive discounts:
   - 1 Pair: DKK 195.00 (50% OFF) - Total: DKK 360.00
   - 2 Pair: DKK 345.00 (40% OFF) - Most Popular
   - 3 Pair: DKK 528.00 (60% OFF)
2. ✅ Interactive bundle selection with visual feedback
3. ✅ Size and color selectors for 1-pair bundle
4. ✅ Real-time price calculation
5. ✅ Custom styled UI components
6. ✅ Responsive mobile-first design
7. ✅ "Add to Cart" functionality with alert confirmation
8. ✅ Free 2-day shipping indicator

## Functional Entry URIs
- `GET /` - Main bundle selection page
- `GET /static/app.js` - Frontend JavaScript for interactivity
- `GET /static/style.css` - Custom styles (if needed)

## Features Not Yet Implemented
1. ❌ Backend API for cart management
2. ❌ Size/color selectors for 2-pair and 3-pair bundles
3. ❌ Product images
4. ❌ Shopping cart persistence (localStorage or database)
5. ❌ Checkout flow
6. ❌ Payment integration
7. ❌ User authentication
8. ❌ Order history
9. ❌ Admin panel for managing products and bundles

## Recommended Next Steps
1. Add product images to each bundle option
2. Implement size/color selectors for all bundle tiers
3. Create backend API endpoints for cart management:
   - `POST /api/cart/add` - Add items to cart
   - `GET /api/cart` - Retrieve cart contents
   - `PUT /api/cart/update` - Update cart items
   - `DELETE /api/cart/remove` - Remove items from cart
4. Add shopping cart page with item list and quantity controls
5. Implement checkout flow with address and payment collection
6. Integrate Cloudflare D1 database for order storage
7. Add user authentication for order tracking
8. Create order confirmation and tracking pages

## Data Architecture
- **Data Models**: 
  - Bundle: { id, name, pairs, price, discount, total }
  - CartItem: { bundleId, size, color, quantity }
- **Storage Services**: Currently using in-memory JavaScript objects. Planned: Cloudflare D1 for persistent storage
- **Data Flow**: 
  - User selects bundle → Frontend updates UI → JavaScript calculates total
  - Add to cart → (Future) POST to API → Store in D1 database

## User Guide
1. **Select a Bundle**: Click on any of the three bundle options (1, 2, or 3 pairs)
2. **Choose Size & Color**: For the 1-pair bundle, select size and color for each item
3. **Review Total**: The total price updates automatically based on your selection
4. **Add to Cart**: Click the "+ Add to Cart" button to confirm your selection
5. **Enjoy Free Shipping**: All orders include free 2-day shipping

## Tech Stack
- **Framework**: Hono (lightweight web framework)
- **Frontend**: HTML, Tailwind CSS, Vanilla JavaScript
- **Platform**: Cloudflare Pages
- **Development**: Vite, PM2
- **Version Control**: Git

## Development Commands
```bash
# Build the project
npm run build

# Start development server (sandbox)
pm2 start ecosystem.config.cjs

# Check service status
pm2 list

# View logs
pm2 logs webapp --nostream

# Restart service
fuser -k 3000/tcp && pm2 restart webapp

# Test locally
curl http://localhost:3000
```

## Deployment
- **Platform**: Cloudflare Pages
- **Status**: ✅ Development Active (Sandbox)
- **Last Updated**: 2026-02-17

## Project Structure
```
webapp/
├── src/
│   ├── index.tsx          # Main Hono application with HTML
│   └── renderer.tsx       # Default renderer (not used)
├── public/
│   └── static/
│       ├── app.js         # Frontend JavaScript
│       └── style.css      # Custom styles
├── ecosystem.config.cjs   # PM2 configuration
├── package.json           # Dependencies and scripts
├── vite.config.ts         # Vite build configuration
├── wrangler.jsonc         # Cloudflare configuration
└── README.md              # This file
```

## Design Features
- **Color Scheme**: Teal primary (#14b8a6), Red for discounts, Gray for text
- **Typography**: Inter font family for modern, clean appearance
- **Interactive Elements**: 
  - Custom radio buttons with teal accent
  - Hover effects on bundle cards
  - Selected state with teal border and background
  - Custom dropdown arrows
- **Responsive**: Mobile-first design that works on all screen sizes
