# Getting Started with NWU At-Risk Student System

## System Overview

This is a complete, production-ready system for identifying and supporting at-risk students at North-West University. It includes:

- **Backend API** (Django)
- **Frontend Dashboard** (React)
- **ML Risk Scoring Engine**
- **Real-time Alerts & Notifications**
- **Analytics & Reporting**
- **Support Coordinator Portal**
- **Monitoring & Logging**

## Current Status

✅ **Repository Created**: https://github.com/TshifTAJ/nwu-at-risk-student-system
✅ **Infrastructure Configured**: Docker Compose setup ready
⏳ **Backend Code**: Core modules to be implemented
⏳ **Frontend Code**: React components to be implemented
⏳ **ML Models**: Training scripts to be implemented

## Quick Setup (5 minutes)

### Prerequisites
- Docker & Docker Compose installed
- 8GB RAM available
- Port 8000, 3000, 5432, 6379, 9200 available

### Step 1: Clone Repository

```bash
git clone https://github.com/TshifTAJ/nwu-at-risk-student-system.git
cd nwu-at-risk-student-system
```

### Step 2: Setup Environment

```bash
cp .env.example .env
```

### Step 3: Start Services

```bash
docker-compose up -d
```

This will start:
- PostgreSQL database (port 5432)
- Redis cache (port 6379)
- Elasticsearch (port 9200)
- Prometheus monitoring (port 9090)
- Grafana dashboards (port 3001)

### Step 4: Access Services

| Service | URL | Status |
|---------|-----|--------|
| Frontend | http://localhost:3000 | Coming soon |
| Backend API | http://localhost:8000/api/ | Coming soon |
| API Docs | http://localhost:8000/api/docs/ | Coming soon |
| Grafana | http://localhost:3001 | Ready (admin/admin) |
| Prometheus | http://localhost:9090 | Ready |

## Implementation Roadmap

### Phase 1: Backend Foundation (Week 1-2)
- [ ] Django project setup
- [ ] Database models (Students, Risk Assessments, Interventions)
- [ ] REST API endpoints
- [ ] Authentication system (JWT)
- [ ] Unit tests

### Phase 2: Core Features (Week 3-4)
- [ ] Risk scoring engine
- [ ] Alert & notification system
- [ ] Intervention management
- [ ] Analytics engine
- [ ] Admin dashboard API

### Phase 3: Frontend (Week 5-6)
- [ ] React project setup
- [ ] Login/authentication flow
- [ ] Student dashboard
- [ ] Faculty advisor portal
- [ ] Support coordinator portal
- [ ] Analytics dashboard

### Phase 4: ML Models (Week 7-8)
- [ ] Data preprocessing pipelines
- [ ] Risk prediction models
- [ ] Anomaly detection
- [ ] Model training & evaluation
- [ ] Model serving API

### Phase 5: Testing & Deployment (Week 9-10)
- [ ] Integration tests
- [ ] Load testing
- [ ] Security testing
- [ ] User acceptance testing
- [ ] Production deployment

## Key Components to Build

### 1. Backend Models (Django)

```python
# Student model
- id, student_number, email, name, phone
- cohort_year, major, current_gpa
- enrollment_status, created_at, updated_at

# Risk Assessment model
- id, student_id, assessment_date
- overall_risk_score (0-100)
- academic_risk, financial_risk, mental_health_risk, social_risk
- risk_factors (JSON), recommendations (JSON)
- created_by, updated_at

# Intervention model
- id, student_id, intervention_type
- assigned_coordinator, start_date, end_date
- status, notes, outcomes
- success_metric, satisfaction_score

# Alert model
- id, student_id, alert_type (critical/high/standard)
- triggered_by (rule/model)
- recipients, acknowledged, resolved
- created_at, resolved_at
```

### 2. API Endpoints

```
/api/auth/
  POST /login
  POST /logout
  GET  /me

/api/students/
  GET  /                    # List students
  GET  /{id}               # Get student
  GET  /{id}/risk/         # Get student risk score
  GET  /{id}/interventions/ # Get student interventions

/api/risk/
  GET  /students/          # List at-risk students
  POST /recalculate/       # Trigger recalculation
  GET  /forecast/          # Get 30/60/90-day forecast

/api/interventions/
  GET  /                   # List all interventions
  POST /                   # Create intervention
  GET  /{id}              # Get intervention
  PATCH/{id}              # Update intervention
  POST /{id}/complete     # Mark complete

/api/analytics/
  GET  /dashboard/        # Executive dashboard
  GET  /cohort/           # Cohort analysis
  GET  /retention/        # Retention metrics
  GET  /equity/           # Equity metrics
```

### 3. Frontend Pages

```
Public Routes:
  /login                  # Login page
  /forgot-password        # Password reset

Student Routes (protected):
  /dashboard              # Student dashboard
  /profile                # Student profile
  /resources              # Support resources
  /appointments           # Appointment booking
  /messages               # Messages/notifications

Faculty Routes (protected):
  /classes                # My classes
  /class/{id}/students    # Class students overview
  /alerts                 # Student alerts
  /resources              # Resource library

Coordinator Routes (protected):
  /caseload               # My cases
  /case/{id}             # Case details
  /tasks                  # My tasks
  /reports                # Generate reports

Admin Routes (protected):
  /analytics              # Institution dashboard
  /cohorts                # Cohort analysis
  /settings               # System settings
  /users                  # User management
```

## Testing Scenarios

Once implemented, test:

1. **User Authentication**
   - Login as student, faculty, coordinator, admin
   - Verify role-based access control

2. **Risk Scoring**
   - Trigger risk recalculation
   - Verify scores update correctly
   - Check alert generation

3. **Intervention Flow**
   - Create intervention for at-risk student
   - Track coordinator progress
   - Record outcomes
   - Verify impact on risk score

4. **Real-time Alerts**
   - Simulate crisis event
   - Verify alert notification
   - Check escalation routing

5. **Analytics**
   - Generate cohort reports
   - Check retention metrics
   - Verify equity indicators

## File Structure to Implement

```
backend/
├── config/
│   ├── settings.py          # Django settings
│   ├── urls.py              # URL routing
│   ├── wsgi.py              # WSGI config
│   └── asgi.py              # Async config
├── core/
│   ├── models.py            # Base models
│   ├── permissions.py       # Custom permissions
│   └── pagination.py        # Pagination classes
├── students/
│   ├── models.py            # Student, Profile models
│   ├── views.py             # ViewSets
│   ├── serializers.py       # DRF serializers
│   ├── urls.py              # App URLs
│   └── tests.py             # Unit tests
├── risk_scoring/
│   ├── models.py            # RiskAssessment model
│   ├── engine.py            # Risk scoring logic
│   ├── views.py             # Risk endpoints
│   └── tests.py
├── interventions/
│   ├── models.py            # Intervention model
│   ├── views.py             # Intervention endpoints
│   ├── serializers.py       # Serializers
│   └── tests.py
├── analytics/
│   ├── models.py            # Analytics models
│   ├── views.py             # Analytics endpoints
│   ├── queries.py           # Complex queries
│   └── reports.py           # Report generation
├── notifications/
│   ├── models.py            # Alert, Notification models
│   ├── tasks.py             # Celery tasks
│   ├── views.py             # Notification endpoints
│   └── handlers.py          # Alert handlers
├── api/
│   ├── urls.py              # Main API router
│   ├── permissions.py       # Custom permissions
│   └── views.py             # Generic views
└── manage.py

frontend/
├── src/
│   ├── components/
│   │   ├── Layout.tsx       # Main layout
│   │   ├── Navbar.tsx       # Navigation
│   │   ├── StudentCard.tsx  # Student component
│   │   ├── RiskBadge.tsx    # Risk score display
│   │   └── AlertBanner.tsx  # Alert display
│   ├── pages/
│   │   ├── Login.tsx        # Login page
│   │   ├── Dashboard.tsx    # Main dashboard
│   │   ├── StudentProfile.tsx
│   │   ├── InterventionForm.tsx
│   │   └── Analytics.tsx    # Analytics page
│   ├── services/
│   │   ├── api.ts           # API client
│   │   ├── auth.ts          # Auth service
│   │   └── students.ts      # Student service
│   ├── store/
│   │   ├── index.ts         # Redux store
│   │   ├── slices/
│   │   │   ├── auth.ts
│   │   │   ├── students.ts
│   │   │   └── alerts.ts
│   ├── hooks/
│   │   ├── useAuth.ts       # Auth hook
│   │   ├── useStudents.ts   # Students hook
│   │   └── useAlerts.ts     # Alerts hook
│   └── App.tsx              # Main app
└── package.json
```

## Next Steps

1. **Backend Development**
   - Start with models in `backend/students/models.py`
   - Implement serializers in `backend/students/serializers.py`
   - Create viewsets in `backend/students/views.py`
   - Write tests as you go

2. **Database Setup**
   - Create migrations: `python manage.py makemigrations`
   - Run migrations: `python manage.py migrate`
   - Create superuser: `python manage.py createsuperuser`

3. **API Testing**
   - Use Postman or curl to test endpoints
   - Access Swagger docs: `http://localhost:8000/api/docs/`

4. **Frontend Development**
   - Build components incrementally
   - Test with mock data first
   - Connect to real API endpoints

5. **ML Models**
   - Start with logistic regression baseline
   - Evaluate on historical data
   - Serve via API endpoint

## Helpful Commands

```bash
# Docker commands
docker-compose up -d              # Start services
docker-compose down               # Stop services
docker-compose logs -f backend    # View backend logs

# Backend commands
python manage.py makemigrations   # Create migrations
python manage.py migrate          # Run migrations
python manage.py createsuperuser  # Create admin
python manage.py seed_data        # Load sample data
python manage.py runserver        # Dev server
pytest                            # Run tests

# Frontend commands
npm install                       # Install dependencies
npm start                         # Dev server
npm test                          # Run tests
npm build                         # Production build
```

## Resources

- Django Docs: https://docs.djangoproject.com/
- DRF Docs: https://www.django-rest-framework.org/
- React Docs: https://react.dev/
- PostgreSQL Docs: https://www.postgresql.org/docs/
- Docker Docs: https://docs.docker.com/

Happy coding! 🎓
