<div align="center">

#  Full E-Commerce APIs 🛒

### Production-Ready RESTful API for Modern E-Commerce Platforms

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-5.0-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6.0+-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Stripe](https://img.shields.io/badge/Stripe-Payment-635BFF?style=for-the-badge&logo=stripe&logoColor=white)](https://stripe.com/)
[![JWT](https://img.shields.io/badge/JWT-Auth-000000?style=for-the-badge&logo=json-web-tokens&logoColor=white)](https://jwt.io/)

**[📚 API Documentation](https://documenter.getpostman.com/view/51642188/2sBXcBoNTo)** 

</div>

---

## 🎯 Overview

A **enterprise-grade** Node.js E-Commerce Backend API featuring advanced authentication, payment processing, and scalable architecture. Built with clean code principles and production-ready security practices.

### ✨ Key Highlights

```typescript
🔐 Dual-Token Authentication    → Access + Refresh Token Rotation
💳 Stripe Integration            → Checkout Sessions + Webhooks
🖼️ Smart Image Processing       → Multer + Sharp Pipeline
🛡️ Military-Grade Security      → JWT, Helmet, XSS Protection, Rate Limiting
📊 Advanced Query Engine         → Filtering, Sorting, Pagination, Search
🏗️ Clean Architecture           → Service Layer + Factory Pattern
🚀 Production Ready              → Error Handling, Logging, Validation
```

---

## 📦 Core Features

<table>
<tr>
<td width="50%">

### 🔐 Authentication System
- **JWT Dual-Token Strategy**
  - Access tokens (15 min expiry)
  - Refresh token rotation
  - Automatic token revocation
- **Password Management**
  - Bcrypt hashing (10 rounds)
  - Reset via email
  - Secure change flow
- **Account Security**
  - Email verification
  - Session management
  - Logout functionality

</td>
<td width="50%">

### 🛍️ Product Management
- **Full CRUD Operations**
  - Categories & Subcategories
  - Brand management
  - Dynamic slug generation
- **Image Processing**
  - Multi-image upload
  - Auto resize (800x800)
  - Sharp optimization
  - CDN-ready URLs
- **Advanced Search**
  - Keyword search
  - Filter by category/brand
  - Price range queries.

</td>
</tr>
<tr>
<td width="50%">

### 🛒 Shopping Experience
- **Smart Cart System**
  - Real-time price calculation
  - Quantity management
  - Persistent storage
- **Coupon Engine**
  - Percentage discounts
  - Expiration handling
  - Single-use validation
- **Wishlist**
  - Save favorite items
  - Quick add to cart
  - Sync across sessions

</td>
<td width="50%">

### 💳 Payment & Orders
- **Stripe Integration**
  - Secure checkout sessions
  - Webhook event handling
  - Payment verification
- **Order Management**
  - Cash on delivery
  - Card payments
  - Order tracking
  - Status updates
- **Auto Inventory**
  - Stock deduction
  - Sold counter
  - Out-of-stock handling

</td>
</tr>
<tr>
<td width="50%">

### ⭐ Review System
- **User Reviews**
  - One review per product
  - Star ratings (1-5)
  - Text comments
- **Aggregation**
  - Average rating calculation
  - Total review count
  - Real-time updates
- **Validation**
  - Ownership verification
  - Purchase validation
  - Duplicate prevention

</td>
<td width="50%">

### 👤 User Management
- **Profile System**
  - Personal information
  - Profile updates
  - Account deletion
- **Address Book**
  - Multiple addresses
  - Default selection
  - Quick checkout
- **Role-Based Access**
  - User permissions
  - Admin privileges
  - Middleware protection

</td>
</tr>
</table>

---

## 🏗️ Architecture

### Tech Stack

```yaml
Runtime:        Node.js v18+
Framework:      Express.js v5.0
Database:       MongoDB v6.0 (Mongoose ODM)
Authentication: JWT (Access + Refresh Tokens)
Payments:       Stripe API
Email:          Nodemailer (SMTP)
File Upload:    Multer (Memory Storage)
Image Process:  Sharp
Security:       Helmet, XSS-Clean, HPP, Mongo-Sanitize
Validation:     Express-Validator
Rate Limiting:  Express-Rate-Limit
Compression:    Compression Middleware
```

### Project Structure

```
📁 Full-Ecommerce-Backend-API/
├── 📁 src/
│   ├── 📁 config/              # Configuration files
│   │   ├── database.js         # MongoDB connection
│   │   └── stripe.js           # Stripe setup
│   ├── 📁 middlewares/         # Express middlewares
│   │   ├── auth.js             # JWT verification
│   │   ├── error.js            # Error handler
│   │   ├── upload.js           # File upload
│   │   └── validation.js       # Input validation
│   ├── 📁 models/              # Mongoose schemas
│   │   ├── User.js
│   │   ├── Product.js
│   │   ├── Category.js
│   │   ├── Order.js
│   │   ├── Review.js
│   │   ├── Cart.js
│   │   └── Coupon.js
│   ├── 📁 routes/              # API routes
│   │   ├── auth.routes.js
│   │   ├── user.routes.js
│   │   ├── product.routes.js
│   │   ├── category.routes.js
│   │   ├── order.routes.js
│   │   └── ...
│   ├── 📁 services/            # Business logic
│   │   ├── auth.service.js
│   │   ├── email.service.js
│   │   ├── payment.service.js
│   │   └── factory.service.js
│   ├── 📁 utils/               # Helper utilities
│   │   ├── ApiError.js
│   │   ├── ApiFeatures.js
│   │   └── asyncHandler.js
│   ├── 📁 validators/          # Request validators
│   │   ├── auth.validator.js
│   │   ├── product.validator.js
│   │   └── ...
│   └── app.js                  # Express app
├── 📁 uploads/                 # Static files
├── server.js                   # Entry point
├── .env                        # Environment variables
├── .gitignore
├── package.json
└── README.md
```

### Request Flow Pipeline

```mermaid
graph LR
    A[Client Request] --> B[CORS]
    B --> C[Rate Limiter]
    C --> D[Body Parser]
    D --> E[Helmet]
    E --> F[XSS Clean]
    F --> G[Sanitize]
    G --> H{Auth Required?}
    H -->|Yes| I[JWT Verify]
    H -->|No| J[Route Handler]
    I --> K{Valid?}
    K -->|No| L[401 Error]
    K -->|Yes| M[Role Check]
    M --> N[Validation]
    N --> J
    J --> O[Service Layer]
    O --> P[Database]
    P --> Q[Response]
```

---

## 🔒 Security Features

<table>
<tr>
<td width="33%">

### 🛡️ Authentication
- JWT with RS256 signing
- Token rotation strategy
- Refresh token blacklist
- Password hashing (bcrypt)
- Rate limiting on auth routes

</td>
<td width="33%">

### 🔐 Input Security
- XSS attack prevention
- NoSQL injection sanitization
- HTTP parameter pollution
- Request size limits
- File type validation

</td>
<td width="33%">

### 🚨 API Security
- Helmet HTTP headers
- CORS configuration
- Rate limiting (100/15min)
- Request validation
- Error message sanitization

</td>
</tr>
</table>

### Security Headers (Helmet)

```javascript
✓ Content-Security-Policy
✓ X-DNS-Prefetch-Control
✓ X-Frame-Options: DENY
✓ X-Content-Type-Options: nosniff
✓ Strict-Transport-Security
✓ X-XSS-Protection
```

---

## 🚀 Getting Started

### Prerequisites

```bash
Node.js >= 18.0.0
MongoDB >= 6.0.0
npm >= 9.0.0
```

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/mahmoud-atta1/Full-Ecommerce-Backend-API.git
cd Full-Ecommerce-Backend-API

# 2. Install dependencies
npm install

# 3. Configure environment variables
cp .env.example .env
# Edit .env with your configuration

# 4. Start MongoDB (if local)
mongod

# 5. Run the application
npm run start:dev
```

### Environment Configuration

Create `.env` file in root directory:

```bash
# Server
NODE_ENV=development
PORT=5000
BASE_URL=http://localhost:5000

# Database
DB_URI=mongodb://localhost:27017/ecommerce
# For MongoDB Atlas:
# DB_URI=mongodb+srv://username:password@cluster.mongodb.net/ecommerce

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-minimum-32-characters-long
JWT_REFRESH_SECRET=your-refresh-token-secret-minimum-32-characters
JWT_EXPIRE_TIME=15m
JWT_REFRESH_EXPIRE_TIME=7d

# Stripe
STRIPE_SECRET_KEY=sk_test_your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=whsec_your_webhook_secret_from_stripe_cli

# Email (Gmail SMTP)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
GOOGLE_APP_PASSWORD=your-16-character-app-password

# Rate Limiting
RATE_LIMIT_WINDOW=15
RATE_LIMIT_MAX_REQUESTS=100
```

### Stripe Webhook Setup (Local Development)

```bash
# 1. Install Stripe CLI
# Download from: https://stripe.com/docs/stripe-cli

# 2. Login to Stripe
stripe login

# 3. Forward webhooks to your local server
stripe listen --forward-to localhost:5000/api/v1/webhooks/stripe

# 4. Copy the webhook signing secret to .env
STRIPE_WEBHOOK_SECRET=whsec_xxxxxxxxxxxxx
```

---

## 📡 API Endpoints

### Base URL

```
http://localhost:5000/api/v1
```

### Endpoint Overview

| Resource | Method | Endpoint | Auth | Description |
|----------|--------|----------|------|-------------|
| **Auth** | POST | `/auth/signup` | ❌ | Register new user |
| | POST | `/auth/login` | ❌ | User login |
| | POST | `/auth/refresh` | ❌ | Refresh access token |
| | POST | `/auth/forgot-password` | ❌ | Request password reset |
| | POST | `/auth/reset-password/:token` | ❌ | Reset password |
| | POST | `/auth/logout` | ✅ | Logout user |
| **Users** | GET | `/users/me` | ✅ | Get current user |
| | PUT | `/users/me` | ✅ | Update profile |
| | PUT | `/users/change-password` | ✅ | Change password |
| | DELETE | `/users/me` | ✅ | Delete account |
| **Products** | GET | `/products` | ❌ | Get all products |
| | GET | `/products/:id` | ❌ | Get single product |
| | POST | `/products` | 👑 | Create product |
| | PUT | `/products/:id` | 👑 | Update product |
| | DELETE | `/products/:id` | 👑 | Delete product |
| **Categories** | GET | `/categories` | ❌ | Get all categories |
| | POST | `/categories` | 👑 | Create category |
| **Cart** | GET | `/cart` | ✅ | Get user cart |
| | POST | `/cart` | ✅ | Add to cart |
| | PUT | `/cart/:itemId` | ✅ | Update quantity |
| | DELETE | `/cart/:itemId` | ✅ | Remove from cart |
| | PUT | `/cart/apply-coupon` | ✅ | Apply coupon |
| **Orders** | GET | `/orders` | ✅ | Get user orders |
| | GET | `/orders/:id` | ✅ | Get single order |
| | POST | `/orders` | ✅ | Create cash order |
| | POST | `/orders/checkout-session` | ✅ | Stripe checkout |
| **Reviews** | GET | `/products/:id/reviews` | ❌ | Get product reviews |
| | POST | `/products/:id/reviews` | ✅ | Create review |
| | PUT | `/reviews/:id` | ✅ | Update review |
| | DELETE | `/reviews/:id` | ✅ | Delete review |
| **Wishlist** | GET | `/wishlist` | ✅ | Get wishlist |
| | POST | `/wishlist` | ✅ | Add to wishlist |
| | DELETE | `/wishlist/:id` | ✅ | Remove from wishlist |
| **Addresses** | GET | `/addresses` | ✅ | Get all addresses |
| | POST | `/addresses` | ✅ | Add address |
| | PUT | `/addresses/:id` | ✅ | Update address |
| | DELETE | `/addresses/:id` | ✅ | Delete address |

**Legend:** ❌ Public | ✅ User Auth Required | 👑 Admin Only

---

## 📝 API Examples

### Authentication

#### Register New User

```bash
curl -X POST http://localhost:5000/api/v1/auth/signup \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "SecurePass123!",
    "passwordConfirm": "SecurePass123!",
    "phone": "+1234567890"
  }'
```

**Response:**
```json
{
  "status": "success",
  "data": {
    "user": {
      "_id": "65a1b2c3d4e5f6a7b8c9d0e1",
      "name": "John Doe",
      "email": "john@example.com",
      "role": "user"
    },
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
}
```

### Advanced Product Search

```bash
# Filter by price range, category, and sort by rating
curl "http://localhost:5000/api/v1/products?price[gte]=100&price[lte]=500&category=electronics&sort=-ratingsAverage&page=1&limit=10"
```

**Query Parameters:**
- `price[gte]=100` - Minimum price
- `price[lte]=500` - Maximum price
- `category=electronics` - Filter by category
- `sort=-ratingsAverage` - Sort by rating (descending)
- `page=1` - Page number
- `limit=10` - Results per page

### Create Order with Stripe

```bash
curl -X POST http://localhost:5000/api/v1/orders/checkout-session \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "shippingAddress": {
      "street": "123 Main St",
      "city": "New York",
      "postalCode": "10001",
      "country": "USA"
    }
  }'
```

**Response:**
```json
{
  "status": "success",
  "session": {
    "id": "cs_test_a1b2c3...",
    "url": "https://checkout.stripe.com/pay/cs_test_a1b2c3..."
  }
}
```

---

## 🎨 Advanced Features

### 1. API Features Chaining

```javascript
// Example: Get top-rated electronics under $500
GET /api/v1/products?category=electronics&price[lte]=500&sort=-ratingsAverage&limit=5

// Supported operations:
- Filtering:     ?field=value
- Comparison:    ?price[gte]=100&price[lte]=500
- Sorting:       ?sort=-price,name
- Pagination:    ?page=2&limit=20
- Field Select:  ?fields=name,price,image
- Search:        ?search=laptop
```

### 2. Image Upload & Optimization

```javascript
// Automatic pipeline:
1. Upload → Multer (Memory Storage)
2. Process → Sharp (Resize 800x800, Convert JPEG, Compress 90%)
3. Save → Local storage (/uploads/products/)
4. Return → Full URL (http://domain.com/uploads/products/image.jpg)

// Supported formats: JPEG, PNG, WEBP
// Max file size: 5MB per image
// Multiple images: Cover + 5 additional images
```

### 3. Smart Cart System

```javascript
// Auto-calculated fields:
- totalPrice: Sum of all items
- totalPriceAfterDiscount: After coupon applied
- Validation: Stock availability check
- Updates: Real-time price changes
```

### 4. Review Aggregation

```javascript
// Automatic calculations on Product model:
- ratingsAverage: Calculated from all reviews
- ratingsQuantity: Total number of reviews
- Updated: On review create/update/delete
```

---

## 📊 Database Schema

### User Model
```javascript
{
  name: String (required),
  email: String (required, unique, lowercase),
  password: String (required, hashed),
  phone: String,
  role: Enum ['user', 'admin'] (default: 'user'),
  active: Boolean (default: true),
  wishlist: [ObjectId],
  addresses: [AddressSchema],
  createdAt: Date,
  updatedAt: Date
}
```

### Product Model
```javascript
{
  name: String (required),
  slug: String (unique, auto-generated),
  description: String (required),
  price: Number (required),
  priceAfterDiscount: Number,
  quantity: Number (required),
  sold: Number (default: 0),
  imageCover: String (required),
  images: [String],
  category: ObjectId (ref: Category),
  subcategory: ObjectId (ref: Subcategory),
  brand: ObjectId (ref: Brand),
  ratingsAverage: Number (default: 0),
  ratingsQuantity: Number (default: 0),
  createdAt: Date,
  updatedAt: Date
}
```

### Order Model
```javascript
{
  user: ObjectId (ref: User),
  items: [{
    product: ObjectId (ref: Product),
    quantity: Number,
    price: Number
  }],
  totalPrice: Number (required),
  shippingAddress: AddressSchema,
  paymentMethod: Enum ['cash', 'card'],
  isPaid: Boolean (default: false),
  paidAt: Date,
  isDelivered: Boolean (default: false),
  deliveredAt: Date,
  createdAt: Date
}
```





---

## 📈 Performance Optimization

- ✅ Database indexing on frequently queried fields
- ✅ Response compression middleware
- ✅ Image optimization pipeline (Sharp)
- ✅ Pagination to limit response size
- ✅ Field selection to reduce payload
- ✅ MongoDB aggregation for complex queries

---

## 🛠️ Development Tools

```json
{
  "scripts": {
    "start": "node server.js",
    "start:dev": "nodemon server.js",
    "start:prod": "NODE_ENV=production node server.js",
    "test": "jest",
    "test:watch": "jest --watch",
    "test:coverage": "jest --coverage",
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

---

## 📚 Documentation

- **[Full API Documentation](https://documenter.getpostman.com/view/51642188/2sBXcBoNTo)** - Complete Postman collection
- **[Postman Collection](docs/ecommerce-api.postman_collection.json)** - Import into Postman

---

## 🤝 Contributing

Contributions are what make the open-source community amazing! Any contributions are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 👨‍💻 Author

**Mahmoud Atta**

- GitHub: [@mahmoud-atta1](https://github.com/mahmoud-atta1)
- Project Link: [Full-Ecommerce-Backend-API](https://github.com/mahmoud-atta1/Full-Ecommerce-Backend-API)

---

<div align="center">

### ⭐ Star this repo if you find it  helpful!

**[⬆ Back to Top](#-full-e-commerce-backend-api)**

Made with ❤️ by Mahmoud Atta

</div>
