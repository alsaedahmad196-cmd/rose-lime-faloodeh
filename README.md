# Rose & Lime Faloodeh - E-Commerce Storefront

A modern, responsive e-commerce storefront for Rose & Lime Faloodeh, a Persian dessert business. Built with React, TypeScript, Vite, and Tailwind CSS.

**Live Demo**: [Your Deployed URL Here]

## 🌟 Features

- **Multi-section SPA**: Home, Story, and Order sections with smooth navigation
- **Product Catalog**: 6 signature faloodeh flavors with detailed descriptions and pricing
- **Shopping Cart**: Add/remove items, adjust quantities, persistent cart using localStorage
- **Order Management**: 
  - Pickup (Kanata South) and Delivery (Westend Ottawa) options
  - Dynamic delivery fees ($5 for orders $35-$74.99, free for $75+)
  - Customer checkout form with validation
- **Order Confirmation**: Receipt display with 24-hour fulfillment notice
- **Catering Info**: Special catering service with 48-hour advance notice requirement
- **Responsive Design**: Fully optimized for mobile, tablet, and desktop
- **Modern UI/UX**: Gradient color scheme, smooth animations, accessible components

## 🛠️ Tech Stack

- **React 18** + TypeScript 5.8 - Modern UI framework
- **Vite 7** - Lightning-fast build tool
- **Tailwind CSS 3.4** - Utility-first CSS framework
- **Lucide React** - Beautiful, consistent icon library
- **Framer Motion** - Smooth animations and transitions
- **React Router** - SPA routing (included in template)

## 📋 Requirements

- Node.js 16+ (18+ recommended)
- npm 8+ or yarn/pnpm

## 🚀 Getting Started

### Local Development

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/rose-lime-faloodeh.git
   cd rose-lime-faloodeh
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start the development server**:
   ```bash
   npm run dev
   ```
   Visit http://localhost:5173 in your browser

4. **Build for production**:
   ```bash
   npm run build
   ```

5. **Preview the production build**:
   ```bash
   npm run preview
   ```

## 📁 Project Structure

```
src/
├── components/
│   ├── FaloodhStore/          # Main storefront components
│   │   ├── Header.tsx         # Navigation bar
│   │   ├── Hero.tsx           # Landing hero section
│   │   ├── Features.tsx        # Business highlights
│   │   ├── ProductList.tsx     # Product grid
│   │   ├── ProductCard.tsx     # Individual product card
│   │   ├── Cart.tsx            # Cart sidebar
│   │   ├── Checkout.tsx        # Checkout modal
│   │   ├── OrderConfirmation.tsx
│   │   ├── Story.tsx           # About us page
│   │   ├── Gallery.tsx         # Image gallery
│   │   ├── Catering.tsx        # Catering section
│   │   ├── Contact.tsx         # Contact form
│   │   ├── CTA.tsx             # Call-to-action
│   │   └── Footer.tsx          # Footer
│   └── mock/                   # Mock data
│       ├── productsData.ts     # Product catalog
│       └── galleryData.ts      # Gallery images
├── utils/
│   └── deliveryConfig.ts       # Delivery logic
├── App.tsx                     # Main app component
├── main.tsx                    # Entry point
└── index.css                   # Global styles
```

## 🎨 Design System

- **Color Palette**: 
  - Primary: `#c3d962` (Lime Green)
  - Secondary: `#e37f8c` (Rose)
  - Sage: `#90af6e`
  - Dark: `#494949`
  - Accent: `#eec7be`
- **Typography**: Inter font family
- **Spacing**: 8-point scale
- **Responsive Breakpoints**: Mobile (375px), Tablet (640px), Desktop (1024px+)

## 🔧 Configuration

- **Vite Config**: `vite.config.ts` - Build settings
- **TypeScript**: `tsconfig.json` - Strict mode enabled
- **Tailwind**: `tailwind.config.js` - Custom color tokens
- **PostCSS**: `postcss.config.js` - Tailwind plugins

## 📦 Deployment

### GitHub Pages
1. Update `vite.config.ts` base path if needed:
   ```typescript
   export default {
     base: '/repository-name/',
     // ...
   }
   ```
2. Push code to GitHub, enable GitHub Pages in repository settings
3. Select `main` branch and `/root` folder

### Vercel / Netlify
1. Connect your GitHub repository
2. Build command: `npm run build`
3. Publish directory: `dist`

### Docker
```dockerfile
FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:18-alpine
WORKDIR /app
RUN npm install -g serve
COPY --from=build /app/dist ./dist
EXPOSE 3000
CMD ["serve", "-s", "dist", "-l", "3000"]
```

## 🔐 Security

- No sensitive data stored in code
- Cart data stored in browser localStorage (not sent to server)
- All external images loaded from secure CDNs
- Form validation before checkout

## 📝 License

MIT License - See [LICENSE](./LICENSE) file for details

## 🤝 Contributing

Contributions welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## 📞 Support

For questions or issues:
- Open an issue on GitHub
- Contact: [Your Contact Email]

## 🎯 Future Enhancements

- [ ] Backend API integration for order persistence
- [ ] User authentication and order history
- [ ] Admin dashboard for order management
- [ ] Email notifications for order confirmations
- [ ] Payment gateway integration
- [ ] Multi-language support (i18n)
- [ ] Order tracking system

---

Built with ❤️ for Rose & Lime Faloodeh
