# NWU At-Risk Student Early Identification & Support System

## Overview
A comprehensive, integrated system for identifying and supporting at-risk students at North-West University (NWU). This system combines predictive analytics, real-time monitoring, intervention tracking, and support coordination to improve student success and retention.

## Key Features

### 1. **Early Identification Module**
- Predictive risk scoring using machine learning
- Multi-factor risk assessment (academic, financial, psychosocial)
- Real-time anomaly detection
- Risk stratification (Low, Medium, High, Critical)

### 2. **Student Analytics Dashboard**
- Comprehensive student profiles
- Academic performance tracking
- Attendance monitoring
- Financial status insights
- Psychosocial indicators

### 3. **Intervention Management**
- Automated intervention recommendations
- Support coordinator assignment
- Intervention tracking and outcomes
- Evidence-based intervention library

### 4. **Support Services Coordination**
- Academic tutoring
- Financial aid counseling
- Mental health support
- Career guidance
- Peer mentoring

### 5. **Analytics & Reporting**
- Real-time dashboards
- Cohort analysis
- Success metrics tracking
- Faculty/staff performance insights
- Predictive forecasting

## Quick Start

### Prerequisites
- Docker & Docker Compose (recommended)
- Or: Python 3.11+, PostgreSQL 14+, Node.js 18+, Redis

### Option 1: Docker Setup (Recommended)

```bash
# Clone repository
git clone https://github.com/TshifTAJ/nwu-at-risk-student-system.git
cd nwu-at-risk-student-system

# Copy environment file
cp .env.example .env

# Start all services
docker-compose up -d

# Run migrations
docker-compose exec backend python manage.py migrate

# Create superuser
docker-compose exec backend python manage.py createsuperuser

# Load sample data (optional)
docker-compose exec backend python manage.py seed_data

# Access services
# Frontend: http://localhost:3000
# Backend API: http://localhost:8000/api/
# Admin: http://localhost:8000/admin/
# Grafana: http://localhost:3001 (admin/admin)
```

### Option 2: Manual Setup

```bash
# Clone repository
git clone https://github.com/TshifTAJ/nwu-at-risk-student-system.git
cd nwu-at-risk-student-system

# Backend Setup
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt

# Configure database
cp .env.example .env
# Edit .env with your database details

python manage.py migrate
python manage.py createsuperuser
python manage.py runserver

# Frontend Setup (new terminal)
cd frontend
npm install
npm start  # Runs on http://localhost:3000
```

## Services & Access Points

| Service | URL | Credentials |
|---------|-----|-------------|
| **Frontend** | http://localhost:3000 | Login with student/coordinator/admin |
| **Backend API** | http://localhost:8000/api/ | JWT Token |
| **Admin Panel** | http://localhost:8000/admin/ | Superuser credentials |
| **API Docs (Swagger)** | http://localhost:8000/api/docs/ | N/A |
| **Grafana Monitoring** | http://localhost:3001 | admin / admin |
| **PostgreSQL** | localhost:5432 | postgres / postgres |
| **Redis** | localhost:6379 | N/A |
| **Elasticsearch** | http://localhost:9200 | N/A |

## Testing the System

### 1. Backend API Testing

```bash
# Run all tests
docker-compose exec backend pytest

# Run specific test module
docker-compose exec backend pytest tests/students/test_models.py

# With coverage report
docker-compose exec backend pytest --cov=backend tests/
```

### 2. Frontend Testing

```bash
# Run frontend tests
cd frontend
npm test

# Run with coverage
npm test -- --coverage
```

### 3. Manual Testing Scenarios

#### Scenario 1: Student Login & View Dashboard
1. Go to http://localhost:3000
2. Login with test student credentials
3. View personal dashboard with risk score, resources, upcoming appointments

#### Scenario 2: Faculty View At-Risk Students
1. Login as faculty member
2. Navigate to "My Classes"
3. View class risk profile and individual student alerts
4. Click on at-risk student to view details and recommendations

#### Scenario 3: Support Coordinator Case Management
1. Login as support coordinator
2. View assigned caseload
3. Click on a student to open case details
4. Create/update intervention record
5. Add follow-up tasks
6. Generate outcome report

#### Scenario 4: Risk Scoring in Action
1. Login as admin
2. Go to Analytics > Risk Scoring
3. Trigger manual risk recalculation
4. View updated risk scores and alerts
5. Check intervention recommendations

#### Scenario 5: Real-time Alerts
1. Simulate critical event (e.g., student failing course)
2. Observe real-time alert notification
3. Verify alert routing to appropriate staff
4. Confirm task creation for follow-up

### 4. Load Testing

```bash
# Using Apache Bench
ab -n 1000 -c 10 http://localhost:8000/api/students/

# Using Locust (install: pip install locust)
# Create locustfile.py with test scenarios
locust -f locustfile.py --host=http://localhost:8000
```

### 5. Database Inspection

```bash
# Connect to PostgreSQL
docker-compose exec db psql -U postgres -d nwu_student_system

# Useful queries
SELECT COUNT(*) FROM students_student;  -- Total students
SELECT COUNT(*) FROM students_riskassessment;  -- Risk assessments
SELECT COUNT(*) FROM interventions_intervention;  -- Interventions
SELECT status, COUNT(*) FROM interventions_intervention GROUP BY status;  -- Intervention status breakdown
```

### 6. Sample Data Loading

```bash
# Load predefined sample data
docker-compose exec backend python manage.py seed_data

# Generate random data for load testing
docker-compose exec backend python manage.py generate_test_data --students 1000 --seed 42
```

## API Endpoints Overview

### Authentication
```
POST   /api/auth/login/           # Student/Staff login
POST   /api/auth/logout/          # Logout
POST   /api/auth/refresh/         # Refresh token
GET    /api/auth/me/              # Current user info
```

### Students
```
GET    /api/students/             # List all students (admin/coordinator)
GET    /api/students/{id}/        # Student detail
GET    /api/students/{id}/profile/ # Full student profile
PATCH  /api/students/{id}/        # Update student info
GET    /api/students/{id}/risk/   # Student risk score
GET    /api/students/{id}/history/ # Academic history
```

### Risk Assessment
```
GET    /api/risk/students/        # List at-risk students
GET    /api/risk/scores/          # Risk scores by cohort
POST   /api/risk/recalculate/     # Trigger recalculation
GET    /api/risk/forecast/        # 30/60/90 day forecast
GET    /api/risk/factors/{id}/    # Risk factor breakdown
```

### Interventions
```
GET    /api/interventions/        # List interventions
POST   /api/interventions/        # Create intervention
GET    /api/interventions/{id}/   # Intervention detail
PATCH  /api/interventions/{id}/   # Update intervention
POST   /api/interventions/{id}/complete/ # Mark complete
GET    /api/interventions/{id}/outcome/  # Outcome tracking
```

### Analytics
```
GET    /api/analytics/dashboard/  # Executive dashboard data
GET    /api/analytics/cohort/     # Cohort analysis
GET    /api/analytics/interventions/ # Intervention effectiveness
GET    /api/analytics/retention/  # Retention metrics
GET    /api/analytics/equity/     # Equity metrics
```

### Notifications
```
GET    /api/notifications/        # User notifications
GET    /api/alerts/               # Active alerts
POST   /api/alerts/{id}/acknowledge/ # Mark alert read
```

## Monitoring & Debugging

### View Logs

```bash
# Backend logs
docker-compose logs -f backend

# Celery worker logs
docker-compose logs -f celery_worker

# All services
docker-compose logs -f
```

### Check Service Health

```bash
# Backend health
curl http://localhost:8000/health/

# Database connection
docker-compose exec backend python manage.py dbshell

# Redis connection
docker-compose exec redis redis-cli ping

# Elasticsearch status
curl http://localhost:9200/_cluster/health?pretty
```

### Performance Monitoring

- Grafana Dashboard: http://localhost:3001
- Prometheus: http://localhost:9090
- Check CPU, memory, request latency, error rates

## File Structure

```
nwu-at-risk-student-system/
├── backend/                    # Django backend
│   ├── core/                  # Core Django app
│   ├── students/              # Student management
│   ├── risk_scoring/          # Risk scoring engine
│   ├── interventions/         # Intervention management
│   ├── analytics/             # Analytics engine
│   ├── notifications/         # Alert & notification system
│   ├── api/                   # REST API endpoints
│   ├── config/                # Django settings
│   ├── tests/                 # Test suite
│   ├── manage.py              # Django CLI
│   └── requirements.txt        # Python dependencies
├── frontend/                   # React frontend
│   ├── src/
│   │   ├── components/        # React components
│   │   ├── pages/             # Page components
│   │   ├── services/          # API services
│   │   ├── store/             # Redux state
│   │   ├── hooks/             # Custom React hooks
│   │   └── App.tsx            # Main app component
│   ├── package.json
│   └── Dockerfile
├── ml_models/                  # Machine learning models
│   ├── risk_prediction/       # Risk prediction models
│   ├── feature_engineering/   # Feature engineering
│   └── model_training/        # Training scripts
├── tests/                      # Integration tests
├── docs/                       # Documentation
├── docker-compose.yml          # Multi-container setup
├── .env.example               # Environment template
└── README.md                  # This file
```

## Troubleshooting

### Port Already in Use
```bash
# Find and kill process using port 8000
sudo lsof -i :8000
sudo kill -9 <PID>
```

### Database Connection Error
```bash
# Check PostgreSQL is running
docker-compose exec db pg_isready

# Reset database
docker-compose exec backend python manage.py flush --no-input
docker-compose exec backend python manage.py migrate
```

### Redis Connection Error
```bash
# Check Redis is running
docker-compose exec redis redis-cli ping

# Flush Redis cache
docker-compose exec redis redis-cli FLUSHALL
```

### Frontend Not Loading
```bash
# Clear node_modules and reinstall
cd frontend
rm -rf node_modules package-lock.json
npm install
npm start
```

## Documentation

- **[Installation Guide](docs/installation/README.md)** - Detailed setup instructions
- **[API Documentation](docs/api/README.md)** - Complete API reference
- **[Architecture Guide](docs/architecture/README.md)** - System design details
- **[User Guides](docs/user_guides/)** - Step-by-step guides for different roles
- **[Development Guide](docs/development/README.md)** - Development setup & guidelines

## Key Technologies

**Backend**: Django 4.2, Python 3.11, PostgreSQL, Redis, Elasticsearch
**Frontend**: React 18, TypeScript, Material-UI, Redux
**ML/Data**: scikit-learn, TensorFlow, pandas, NumPy
**DevOps**: Docker, Kubernetes, GitHub Actions, Prometheus, Grafana

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## License

MIT License - See [LICENSE](LICENSE) for details.

## Support & Contact

For issues, questions, or suggestions:
- Open an issue on GitHub
- Contact the development team
- See [docs/support/](docs/support/) for troubleshooting

## Next Steps

1. ✅ Clone the repository
2. ✅ Setup environment variables
3. ✅ Run `docker-compose up -d`
4. ✅ Access http://localhost:3000
5. ✅ Login with test credentials
6. ✅ Explore the system
7. 📖 Read the documentation
8. 🧪 Run the tests
9. 🚀 Deploy to production

Happy coding! 🎓
