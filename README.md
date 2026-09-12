# NWU At-Risk Student Early Identification & Support System

## Overview
A comprehensive, integrated system for identifying and supporting at-risk students at North-West University (NWU). This system combines predictive analytics, real-time monitoring, intervention tracking, and support coordination to improve student success and retention.

## 🎯 Key Features

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

## 🚀 Quick Start

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
# Backend Setup
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver

# Frontend Setup (new terminal)
cd frontend
npm install
npm start
```

## 📊 Services & Access Points

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

## 🧪 Testing

### Backend Tests
```bash
docker-compose exec backend pytest
docker-compose exec backend pytest tests/students/test_models.py
docker-compose exec backend pytest --cov=backend tests/
```

### Frontend Tests
```bash
cd frontend
npm test
npm test -- --coverage
```

### Manual Test Scenarios

#### Scenario 1: Student Login & Dashboard
1. Go to http://localhost:3000
2. Login with test student credentials
3. View personal dashboard with risk score and resources

#### Scenario 2: Faculty View At-Risk Students
1. Login as faculty member
2. Navigate to "My Classes"
3. View class risk profiles
4. Click on at-risk student for details

#### Scenario 3: Support Coordinator Case Management
1. Login as support coordinator
2. View assigned caseload
3. Create/update intervention
4. Add follow-up tasks
5. Record outcomes

#### Scenario 4: Real-time Alerts
1. Simulate critical event
2. Observe alert notification
3. Verify alert routing
4. Confirm task creation

## 📁 Project Structure

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
│   ├── manage.py
│   └── requirements.txt
├── frontend/                   # React frontend
│   ├── src/
│   │   ├── components/        # React components
│   │   ├── pages/             # Page components
│   │   ├── services/          # API services
│   │   ├── store/             # Redux state
│   │   ├── hooks/             # Custom hooks
│   │   └── App.tsx
│   ├── package.json
│   └── Dockerfile
├── ml_models/                  # Machine learning models
│   ├── risk_prediction/       # Risk prediction models
│   ├── feature_engineering/   # Feature engineering
│   └── model_training/        # Training scripts
├── tests/                      # Integration tests
├── docs/                       # Documentation
├── docker-compose.yml          # Multi-container setup
├── .env.example                # Environment template
└── README.md                   # This file
```

## 🔧 Technology Stack

**Backend**: Django 4.2, Python 3.11, PostgreSQL, Redis, Elasticsearch
**Frontend**: React 18, TypeScript, Material-UI, Redux
**ML/Data**: scikit-learn, TensorFlow, pandas, NumPy
**DevOps**: Docker, Kubernetes, GitHub Actions, Prometheus, Grafana

## 📚 Documentation

- [Installation Guide](docs/installation/README.md)
- [API Documentation](docs/api/README.md)
- [Architecture Guide](docs/architecture/README.md)
- [User Guides](docs/user_guides/)
- [Development Guide](docs/development/README.md)
- [Getting Started](GETTING_STARTED.md)
- [Project Overview](PROJECT_OVERVIEW.md)

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## 📄 License

MIT License - See [LICENSE](LICENSE) for details.

## 💬 Support

For issues, questions, or suggestions:
- Open an issue on [GitHub Issues](https://github.com/TshifTAJ/nwu-at-risk-student-system/issues)
- See [docs/support/](docs/support/) for troubleshooting

## 🎓 Next Steps

1. ✅ Clone the repository
2. ✅ Setup environment variables
3. ✅ Run `docker-compose up -d`
4. ✅ Access http://localhost:3000
5. ✅ Login with test credentials
6. 📖 Read the documentation
7. 🧪 Run the tests
8. 🚀 Deploy to production

Happy coding! 🎉
