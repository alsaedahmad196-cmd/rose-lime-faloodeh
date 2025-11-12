# Rose & Lime Faloodeh - React Storefront

A modern React-based e-commerce storefront for Rose & Lime Faloodeh, a Persian dessert business. Built with TypeScript, Vite, and Tailwind CSS.

## Project Status

- **Project Type**: React + TypeScript Modern Web Application (Vite)
- **Entry Point**: `src/main.tsx`
- **Build System**: Vite 7.0.0
- **Styling System**: Tailwind CSS 3.4.17
- **Current Color Palette**: Primary #c3d962, Secondary #e37f8c, Sage #90af6e, Dark #494949, Accent #eec7be

## Development Commands

```bash
# Install dependencies (required before first run)
npm install

# Start local development server (runs on http://localhost:5173)
npm run dev

# Build for production (creates optimized dist/ folder)
npm run build

# Preview production build locally (serves from dist/)
npm run preview
```

## Architecture Overview

### Component Structure

The application is organized as a single-page application (SPA) with modular, reusable React components in `src/components/FaloodhStore/`:

**Core Components:**
- **App.tsx** - Main application component managing all state (cart, order type, checkout flow, active section)
- **Header** - Sticky navigation bar with section switcher (Home, Our Story, Order)
- **Hero** - Landing page hero section with CTA buttons
- **Features** - Highlights of the business (authentication, ingredients, handcrafted)
- **ProductList** - Product grid container rendering all products
- **ProductCard** - Individual product card with sizes, prices, and add-to-cart button
- **Cart** - Sidebar cart summary with item management and order type selector
- **Checkout** - Modal form for collecting customer information (name, phone, email, address, notes)
- **OrderConfirmation** - Modal displaying order receipt confirmation
- **Story** - "About Us" page with business narrative and gallery
- **Gallery** - Responsive 5-image gallery (mobile: 5 cols, tablet: 3 cols, desktop: 5 cols)
- **Catering** - Catering section with contact info (phone, email), and 48-hour advance notice requirement
- **CTA** - Call-to-action section prompting order placement
- **Contact** - Contact form with message capability
- **Footer** - Contact info and copyright

**Data Layer:**
- `src/components/mock/productsData.ts` - Mock product array with 6 signature faloodeh flavors
- `src/components/mock/galleryData.ts` - Gallery image data with alt text and URLs

**Utilities:**
- `src/utils/deliveryConfig.ts` - Delivery fee calculation, location constants, and fulfillment rules

### Application Flow

1. User lands on **Home** section (Hero + Features)
2. User clicks "Order Now" → navigates to **Order** section
3. User browses products and adds items to cart
4. Cart displays with item management and order type toggle (pickup/delivery)
5. User clicks "Proceed to Checkout" → Checkout modal appears
6. User fills form and submits → Order confirmation modal displays
7. Cart persists to localStorage automatically

### State Management

- **cartItems**: Array of CartItem objects (id, name, size, price, qty)
- **orderType**: "pickup" or "delivery" (affects total calculation and address requirement)
- **showCheckout**: Boolean controlling checkout modal visibility
- **orderConfirmation**: Contains order data and total for confirmation display
- **activeSection**: Tracks current page (home, story, order)

**Cart Persistence:**
- Cart is automatically saved to localStorage whenever items change
- Cart is restored on page load from localStorage

## Key Features Implemented

### Core Functionality
- ✅ Multi-section SPA with smooth navigation (Home, Story, Order)
- ✅ Product catalog with 6 signature faloodeh flavors
- ✅ Dynamic cart with add/remove/quantity adjustment
- ✅ Order type selection (Pickup vs Delivery with dynamic fees)
- ✅ Delivery fee logic: $5 fee for orders $35-$74.99, FREE for orders $75+
- ✅ Location-specific fulfillment: Pickup at Kanata South, Delivery to Westend Ottawa
- ✅ Customer checkout form with validation
- ✅ Order confirmation UI with 24-hour fulfillment notice
- ✅ Catering section with contact info and 48-hour notice
- ✅ localStorage persistence for cart
- ✅ Responsive gallery on Story page

### Delivery & Fulfillment
- **Pickup**: Kanata South location, no delivery fee
- **Delivery**: Westend Ottawa only
  - Minimum order: $35
  - Delivery fee: $5 (orders $35-$74.99)
  - Free delivery: Orders $75+
  - Fee validation happens at checkout submission

### UI/UX
- ✅ Responsive design (mobile, tablet, desktop)
- ✅ Gradient color scheme with new palette
- ✅ Lucide React icons throughout
- ✅ Smooth transitions and hover effects
- ✅ Sticky header and sidebar cart
- ✅ Modal dialogs for checkout and confirmation
- ✅ Coming Soon box with gradient background

## Type Definitions

Key TypeScript interfaces in `src/components/`:

```typescript
// Product
interface Product {
  id: number;
  name: string;
  description: string;
  ingredients: string;
  prices: { size: string; price: number }[];
  image: string;
  badge?: string;
  variants?: string[];
}

// Cart Item
interface CartItem {
  id: number;
  name: string;
  size: string;
  price: number;
  qty: number;
}

// Order Data
interface OrderData {
  name: string;
  phone: string;
  email?: string;
  address?: string;
  notes?: string;
  orderType: "pickup" | "delivery";
}
```

## Gallery System (Story Page)

The Story page features a responsive 5-image gallery:

**Responsive Design:**
- Mobile (375px): 5 columns, 2px gap
- Tablet (640px+): 3 columns, 3px gap
- Desktop (1024px+): 5 columns, 4px gap

**Gallery Images:**
1. Persian Heritage (Youware CDN)
2. Traditional Preparation (Youware CDN)
3. Rose Water Essence (Pixabay)
4. Family Moments (Pixabay)
5. Cultural Tradition (Youware CDN)

## Build and Deployment

- **Build Output**: `dist/` directory (optimized production bundle)
- **Build Size**: ~230KB JS, ~30KB CSS (gzipped: 61KB + 5KB)
- **Browser Support**: Modern browsers (ES2020+)
- **Deployment**: Ready for Vercel, Netlify, GitHub Pages, or any static host

## Configuration Files

- `vite.config.ts` - Vite build configuration
- `tsconfig.json` - TypeScript settings (strict mode)
- `tailwind.config.js` - Tailwind CSS customization with custom color tokens
- `postcss.config.js` - PostCSS plugins (Tailwind, Autoprefixer)
- `yw_manifest.json` - Youware project manifest
- `.gitignore` - Git exclusions (node_modules, dist, logs)

## Code Quality Standards

- TypeScript strict mode enabled
- Props-driven component design
- Single responsibility principle
- Semantic HTML and accessibility-conscious markup
- Tailwind CSS for styling (no external CSS files)

## Important Notes

⚠️ **Do NOT modify `index.html` entry point** - The line `<script type="module" src="/src/main.tsx"></script>` is critical and must remain unchanged.

✅ **Asset Paths** - All product and hero images use external URLs (CDNs). No local assets required. Images referenced in `public/` are included in build.

✅ **Currency** - Prices display in CAD using Intl.NumberFormat (e.g., $15.00 CAD).

✅ **Time-Based** - Footer year updates dynamically based on current date.

## GitHub Deployment Checklist

**Before First Upload:**
- [x] `.gitignore` configured (node_modules, dist, logs excluded)
- [x] `README.md` updated with project-specific instructions
- [x] `LICENSE` file added (MIT License)
- [x] Production build verified: `npm run build` succeeds
- [x] Build artifacts (dist/) created and ready
- [x] Log files cleaned up

**When Uploading to GitHub:**
1. Create new repository on GitHub (no README, .gitignore, license initially)
2. Clone locally: `git clone https://github.com/yourusername/rose-lime-faloodeh.git`
3. Copy project files into cloned directory
4. Run initial setup:
   ```bash
   npm install
   npm run build
   ```
5. Commit and push:
   ```bash
   git add .
   git commit -m "Initial commit: Rose & Lime Faloodeh storefront"
   git push -u origin main
   ```

**After Upload (Recommended):**
1. **Add GitHub Actions CI/CD** (`.github/workflows/build.yml`):
   - Runs on every push: install → build → verify
   - Helps catch issues early
2. **Enable GitHub Pages** (optional):
   - Settings → Pages → Deploy from `dist/` branch
   - Or use Actions to auto-deploy built artifacts
3. **Add Topics**: `react`, `ecommerce`, `tailwindcss`, `vite`
4. **Write Discussions/Issues** as needed for feature tracking

## Next Steps (Future Backend Integration)

1. **Backend API Integration** (when ready):
   - Replace localStorage with API calls to persist orders
   - Use Youware Backend or Firebase for data storage
   - Add authentication for customer accounts
   - Implement order status tracking

2. **Recommended Backend Features**:
   - POST `/api/orders` - Submit customer order
   - GET `/api/orders/:id` - Retrieve order status
   - User authentication and order history
   - Admin dashboard for order management

3. **When adding backend**:
   - Follow the Backend Integration Skill workflow
   - Modify checkout submission to call API instead of showing confirmation only
   - Add order status tracking page
   - Keep mock data in dev for testing

## Common Development Tasks

**Add a new product flavor:**
1. Edit `src/components/mock/productsData.ts`
2. Add new Product object to PRODUCTS array
3. Run `npm run build` to verify
4. Test in Order section

**Change color palette:**
1. Update `tailwind.config.js` theme.extend.colors
2. Update component className references (optional, depends on usage)
3. Run `npm run build` to verify

**Update gallery images:**
1. Edit `src/components/mock/galleryData.ts`
2. Replace image URLs (ensure CORS-friendly sources)
3. Update alt text for accessibility
4. Run `npm run build` to verify

**Deploy to production:**
1. `npm run build` - Create optimized dist/
2. Push to GitHub
3. Connect to Vercel/Netlify or enable GitHub Pages
4. Service automatically deploys from dist/

## Troubleshooting

**Build fails with TypeScript errors:**
- Check `tsconfig.json` configuration
- Verify all imports are correct
- Run `npm install` to ensure dependencies are installed

**Images not loading in production:**
- Verify image URLs are absolute (not relative paths)
- Check CORS headers on image source
- Use public CDN URLs when possible

**Cart not persisting:**
- Check browser localStorage is enabled
- Clear browser cache and retry
- Verify localStorage code in App.tsx is not modified

**Styling issues:**
- Run `npm run build` to regenerate Tailwind classes
- Clear dist/ and rebuild: `rm -rf dist && npm run build`
- Verify color names match `tailwind.config.js`
