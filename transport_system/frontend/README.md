# 🚍 Smart Bus Transport Management System

A comprehensive, full-stack bus transport management platform built with **Django REST Framework** (backend) and **React** (frontend), designed to streamline urban public transportation operations in Uganda.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [User Roles](#user-roles)
- [Key Functionalities](#key-functionalities)
- [Installation](#installation)
- [API Documentation](#api-documentation)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

This Smart Bus Transport Management System is designed to modernize and digitize public bus transportation, providing real-time journey tracking, seamless booking, digital payments, and comprehensive analytics for administrators, drivers, and passengers.

The system supports multiple routes across Uganda (Kampala-Entebbe, Kampala-Jinja, Kampala-Mbarara, etc.) with features like:
- Real-time bus tracking and passenger tap-in/tap-out
- Digital wallet for cashless payments
- Route optimization and journey scheduling
- Driver performance monitoring
- Passenger ratings and feedback system
- Comprehensive admin analytics dashboard

## ✨ Features

### For Passengers 👥
- **Digital Wallet**: Top-up and manage wallet balance for seamless payments
- **Journey Booking**: Browse and book journeys on various routes
- **Real-time Tracking**: Track your booked bus in real-time on the map
- **Tap-in System**: Digital boarding pass with QR code for easy tap-in
- **Journey History**: View all past and upcoming journeys
- **Rating & Feedback**: Rate drivers, buses, and overall service quality
- **Notifications**: Get alerts for journey updates, booking confirmations, and wallet transactions

### For Drivers 🚌
- **Journey Dashboard**: View assigned journeys with real-time passenger counts
- **Tap-in Monitoring**: See live passenger tap-ins with instant notifications
- **Occupancy Tracking**: Real-time occupancy percentage with visual progress bars
- **Earnings Dashboard**: 
  - Daily, weekly, and monthly earnings breakdown
  - Journey-by-journey earnings tracking
  - Performance metrics and ratings
- **Journey Management**: Mark journeys as completed or cancel with reasons
- **Passenger Ratings**: View detailed ratings and comments from passengers
- **Bus Assignment**: See assigned buses with status and capacity

### For Administrators 🛠️
- **Comprehensive Dashboard**: 
  - System-wide overview with key metrics
  - Advanced analytics with revenue trends
  - Journey status monitoring (scheduled, in-progress, completed, cancelled)
  - Passenger insights and wallet statistics
- **Bus Management**: 
  - Add, update, and assign buses
  - Monitor bus status (active, maintenance, inactive)
  - Track bus utilization rates
- **Driver Management**:
  - Assign drivers to buses
  - Monitor driver performance and earnings
  - Track on-time rates and ratings
- **Passenger Management**:
  - View all passengers with detailed profiles
  - Wallet top-up functionality
  - Travel history and statistics
- **Journey Management**:
  - Create and schedule journeys
  - Assign buses to routes
  - Edit journey details (departure, arrival, fare, seats)
  - Monitor journey completion rates
- **Route Management**:
  - Create and manage routes with multiple stops
  - Set base fares and route types (express, regular, luxury)
- **Analytics & Reporting**:
  - Revenue by route analysis
  - Daily performance charts
  - Top performing drivers leaderboard
  - System alerts and recommendations
  - Peak hours identification

## 🛠️ Tech Stack

### Backend
- **Framework**: Django 4.x with Django REST Framework
- **Database**: PostgreSQL / SQLite (development)
- **Authentication**: Token-based authentication
- **Payment Integration**: Digital wallet system
- **Real-time Features**: WebSocket support for live updates

### Frontend
- **Framework**: React 18+ with Hooks
- **Styling**: Tailwind CSS
- **State Management**: React Context API (useAuth)
- **Routing**: React Router v6
- **Icons**: Lucide React
- **HTTP Client**: Fetch API with custom apiRequest wrapper
- **Maps**: Google Maps integration for route tracking
- **Charts**: Custom-built visualization components

### Additional Tools
- **Version Control**: Git & GitHub
- **API Testing**: Postman
- **Code Quality**: ESLint, Prettier

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     Frontend (React)                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌─────────┐ │
│  │ Passenger│  │  Driver  │  │  Admin   │  │  Auth   │ │
│  │Dashboard │  │Dashboard │  │Dashboard │  │ Pages   │ │
│  └──────────┘  └──────────┘  └──────────┘  └─────────┘ │
└─────────────────────────────────────────────────────────┘
                          │
                          │ REST API
                          ▼
┌─────────────────────────────────────────────────────────┐
│              Backend (Django REST Framework)            │
│  ┌────────────────────────────────────────────────────┐ │
│  │              API Endpoints                          │ │
│  │  /auth/  /buses/  /journeys/  /payments/  /routes/ │ │
│  └────────────────────────────────────────────────────┘ │
│  ┌────────────────────────────────────────────────────┐ │
│  │              Business Logic Layer                   │ │
│  │  Authentication │ Journey Management │ Payments    │ │
│  └────────────────────────────────────────────────────┘ │
│  ┌────────────────────────────────────────────────────┐ │
│  │              Database (PostgreSQL)                  │ │
│  │  Users │ Buses │ Journeys │ Bookings │ Payments   │ │
│  └────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────┘
```

## 👥 User Roles

### 1. Passenger
- Register and manage profile
- Book journeys and make payments
- Track buses in real-time
- Rate services and provide feedback

### 2. Driver
- View assigned journeys and buses
- Monitor passenger tap-ins
- Track earnings and performance
- Manage journey status

### 3. Administrator
- Full system control and oversight
- Manage buses, drivers, passengers, and journeys
- Access comprehensive analytics
- Generate reports and insights

## 🔑 Key Functionalities

### Journey Booking Flow
1. Passenger browses available journeys
2. Selects route, date, and seats
3. Confirms booking with wallet payment
4. Receives booking confirmation with QR code
5. Taps in at boarding using QR code
6. Journey tracked in real-time
7. Automatic completion upon arrival
8. Rate and review the journey

### Driver Journey Flow
1. Driver logs in and views assigned journeys
2. Monitors real-time passenger tap-ins
3. Receives notifications for new boardings
4. Tracks occupancy percentage
5. Marks journey as completed
6. Views earnings and passenger ratings

### Admin Operations Flow
1. Create routes with stops and fares
2. Add and assign buses to drivers
3. Schedule journeys on routes
4. Monitor system-wide performance
5. Analyze revenue and usage patterns
6. Generate reports and insights

## 📦 Installation

### Prerequisites
- Python 3.9+
- Node.js 16+
- PostgreSQL (or SQLite for development)
- Git

### Backend Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/bus-transport-system.git
cd bus-transport-system/backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Edit .env with your database credentials and secret key

# Run migrations
python manage.py makemigrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Load sample data (optional)
python manage.py loaddata sample_data.json

# Run development server
python manage.py runserver
```

### Frontend Setup

```bash
# Navigate to frontend directory
cd ../frontend

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
# Edit .env with your API base URL

# Start development server
npm start
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:8000
- Admin Panel: http://localhost:8000/admin

## 📚 API Documentation

### Authentication Endpoints
```
POST   /api/auth/register/          # Register new user
POST   /api/auth/login/             # User login
POST   /api/auth/logout/            # User logout
GET    /api/auth/user/              # Get current user
```

### Journey Endpoints
```
GET    /api/journeys/journeys/                    # List all journeys
POST   /api/journeys/journeys/                    # Create journey (admin)
GET    /api/journeys/journeys/{id}/               # Get journey details
PUT    /api/journeys/journeys/{id}/               # Update journey (admin)
DELETE /api/journeys/journeys/{id}/               # Delete journey (admin)
POST   /api/journeys/complete/{id}/               # Complete journey (driver)
POST   /api/journeys/cancel/{id}/                 # Cancel journey
GET    /api/journeys/journeys/{id}/ratings/       # Get journey ratings
POST   /api/journeys/journeys/{id}/ratings/       # Rate journey
GET    /api/journeys/journeys/{id}/driver_status/ # Get driver status
GET    /api/journeys/driver-journeys/             # Get driver's journeys
GET    /api/journeys/journeys/driver-bus-summary/ # Get bus summary
```

### Booking Endpoints
```
GET    /api/journeys/bookings/           # List user bookings
POST   /api/journeys/bookings/           # Create booking
GET    /api/journeys/bookings/{id}/      # Get booking details
POST   /api/journeys/bookings/{id}/tapin/ # Tap-in to journey
DELETE /api/journeys/bookings/{id}/      # Cancel booking
```

### Bus Endpoints
```
GET    /api/buses/admin-buses/      # List all buses (admin)
GET    /api/buses/driver-buses/     # List driver's buses
POST   /api/buses/assign-driver/    # Assign driver to bus
PATCH  /api/buses/{id}/update_status/ # Update bus status
```

### Payment Endpoints
```
GET    /api/payments/wallet/                # Get wallet balance
POST   /api/payments/wallet/topup/{id}/     # Top-up wallet (admin)
GET    /api/payments/transactions/          # Get transactions
```

### Route Endpoints
```
GET    /api/routes/routes/          # List all routes
POST   /api/routes/routes/          # Create route (admin)
GET    /api/routes/routes/{id}/     # Get route details
PUT    /api/routes/routes/{id}/     # Update route (admin)
```

### Admin Endpoints
```
GET    /api/admin/overview-counts/  # Get system overview counts
GET    /api/auth/drivers/           # List all drivers
GET    /api/auth/passengers/        # List all passengers
```

## 🎨 Screenshots

### Passenger Dashboard
- Journey browsing and booking interface
- Real-time bus tracking on map
- Wallet management and transaction history
- Booking history with QR codes
- Rating and feedback system

### Driver Dashboard
- Journey cards with real-time passenger counts
- Occupancy progress bars
- Earnings dashboard with daily/weekly/monthly breakdown
- Performance metrics and ratings
- Passenger feedback display

### Admin Dashboard
- System overview with key metrics
- Advanced analytics with charts
- Bus, driver, and passenger management
- Journey scheduling and management
- Revenue analysis by route
- Top performers leaderboard

## 🚀 Future Enhancements

- [ ] Mobile app (React Native)
- [ ] Push notifications
- [ ] Advanced route optimization with AI
- [ ] Multi-language support
- [ ] Integration with mobile money (MTN, Airtel)
- [ ] Seat selection feature
- [ ] Emergency alert system
- [ ] Weather-based journey recommendations
- [ ] Loyalty rewards program
- [ ] Fleet maintenance scheduling

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Developer

**Vanessa Tendo Nalwoga**
- GitHub: [@Veec0d3s](https://github.com/Veec0d3s)
- Email: vanessatendo0@gmail.com
- University: ISBAT University, Kampala (Class of 2025)
- Degree: First Class Computer Science

## 🙏 Acknowledgments

- ISBAT University for academic support
- The open-source community for amazing tools and libraries
- Beta testers and early users for valuable feedback

## 📞 Support

For support, email vanessatendo0@gmail.com or open an issue in the GitHub repository.

---

**Built with ❤️ in Kampala, Uganda** 🇺🇬
