# Getting Started with NWU At-Risk Student System

## System Overview

This is a complete, production-ready system for identifying and supporting at-risk students at North-West University. It includes:

- **Backend API** (Django REST Framework)
- **Frontend Dashboard** (React)
- **ML Risk Scoring Engine**
- **Real-time Alerts & Notifications**
- **Analytics & Reporting**
- **Support Coordinator Portal**
- **Monitoring & Logging** (Prometheus/Grafana)

## Current Status

✅ **Repository**: https://github.com/TshifTAJ/nwu-at-risk-student-system
✅ **Infrastructure**: Docker Compose setup ready
⏳ **Backend Code**: Core modules ready for implementation
⏳ **Frontend Code**: React components ready for implementation
⏳ **ML Models**: Training scripts ready for implementation

## Quick Setup (5 minutes)

### Prerequisites
- Docker & Docker Compose installed
- 8GB RAM available
- Ports 8000, 3000, 5432, 6379, 9200 available

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

## System Architecture

```
┌─────────────────────────────────────────┐
│     Data Integration Layer              │
│  (Student Management, Academic, Health) │
└─────────────┬───────────────────────────┘
              │
┌─────────────▼───────────────────────────┐
│     Data Warehouse & ETL Pipeline       │
│  (PostgreSQL, Redis, Elasticsearch)     │
└─────────────┬───────────────────────────┘
              │
     ┌────────┼────────┐
     │        │        │
┌────▼─┐  ┌──▼──┐  ┌──▼──────┐
│ Risk │  │Rules│  │ Machine  │
│Engine│  │Engine  │Learning  │
└────┬─┘  └──┬──┘  └──┬───────┘
     │      │        │
     └──────┼────────┘
            │
     ┌──────▼──────┐
     │ Risk Scoring │
     │   Engine    │
     └──────┬──────┘
            │
   ┌────────┼────────┐
   │        │        │
┌──▼──┐  ┌─▼───┐  ┌─▼──────┐
│Alert │  │Alert  │  │Support │
│Notif.│  │Engine │  │Coord.  │
└──────┘  └───────┘  └────────┘
```

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

## Core Modules to Build

### 1. Backend Models (Django)

**Student Model**
```python
- id, student_number, email, name, phone
- cohort_year, major, current_gpa
- enrollment_status, created_at, updated_at
```

**Risk Assessment Model**
```python
- id, student_id, assessment_date
- overall_risk_score (0-100)
- academic_risk, financial_risk, mental_health_risk, social_risk
- risk_factors (JSON), recommendations (JSON)
```

**Intervention Model**
```python
- id, student_id, intervention_type
- assigned_coordinator, start_date, end_date
- status, notes, outcomes
- success_metric, satisfaction_score
```

**Alert Model**
```python
- id, student_id, alert_type (critical/high/standard)
- triggered_by (rule/model), recipients
- acknowledged, resolved, created_at
```

### 2. API Endpoints

```
Authentication:
POST   /api/auth/login
POST   /api/auth/logout
GET    /api/auth/me

Students:
GET    /api/students/
GET    /api/students/{id}
GET    /api/students/{id}/risk/
GET    /api/students/{id}/interventions/

Risk:
GET    /api/risk/students/
POST   /api/risk/recalculate/
GET    /api/risk/forecast/

Interventions:
GET    /api/interventions/
POST   /api/interventions/
GET    /api/interventions/{id}
PATCH  /api/interventions/{id}
POST   /api/interventions/{id}/complete

Analytics:
GET    /api/analytics/dashboard/
GET    /api/analytics/cohort/
GET    /api/analytics/retention/
GET    /api/analytics/equity/
```

### 3. Frontend Pages

**Public Routes**
- `/login` - Login page
- `/forgot-password` - Password reset

**Student Routes**
- `/dashboard` - Student dashboard
- `/profile` - Student profile
- `/resources` - Support resources
- `/appointments` - Appointment booking

**Faculty Routes**
- `/classes` - My classes
- `/class/{id}/students` - Class students
- `/alerts` - Student alerts

**Coordinator Routes**
- `/caseload` - My cases
- `/case/{id}` - Case details
- `/tasks` - My tasks
- `/reports` - Generate reports

**Admin Routes**
- `/analytics` - Institution dashboard
- `/cohorts` - Cohort analysis
- `/settings` - System settings

## Testing Scenarios

### 1. User Authentication
- [ ] Login as student
- [ ] Login as faculty
- [ ] Login as coordinator
- [ ] Login as admin
- [ ] Verify role-based access control

### 2. Risk Scoring
- [ ] Trigger risk recalculation
- [ ] Verify scores update
- [ ] Check alert generation
- [ ] View score breakdown

### 3. Intervention Flow
- [ ] Create intervention
- [ ] Assign coordinator
- [ ] Track progress
- [ ] Record outcomes
- [ ] Verify impact on risk score

### 4. Real-time Alerts
- [ ] Simulate crisis event
- [ ] Verify alert notification
- [ ] Check escalation routing
- [ ] Confirm task creation

### 5. Analytics
- [ ] Generate cohort reports
- [ ] Check retention metrics
- [ ] Verify equity indicators
- [ ] Review intervention effectiveness

## Development Commands

### Docker Commands
```bash
docker-compose up -d              # Start services
docker-compose down               # Stop services
docker-compose logs -f backend    # View backend logs
docker-compose exec backend bash  # Connect to backend
```

### Backend Commands
```bash
python manage.py makemigrations   # Create migrations
python manage.py migrate          # Run migrations
python manage.py createsuperuser  # Create admin
python manage.py seed_data        # Load sample data
python manage.py runserver        # Dev server
pytest                            # Run tests
```

### Frontend Commands
```bash
npm install                       # Install dependencies
npm start                         # Dev server
npm test                          # Run tests
npm build                         # Production build
```

## Resources

- [Django Documentation](https://docs.djangoproject.com/)
- [Django REST Framework](https://www.django-rest-framework.org/)
- [React Documentation](https://react.dev/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Docker Documentation](https://docs.docker.com/)
- [GitHub Actions](https://github.com/features/actions)

## Troubleshooting

### Port Already in Use
```bash
sudo lsof -i :8000
sudo kill -9 <PID>
```

### Database Connection Error
```bash
docker-compose exec db pg_isready
docker-compose exec backend python manage.py flush --no-input
```

### Redis Connection Error
```bash
docker-compose exec redis redis-cli ping
docker-compose exec redis redis-cli FLUSHALL
```

### Frontend Not Loading
```bash
cd frontend
rm -rf node_modules package-lock.json
npm install
npm start
```

## Next Steps

1. Verify Docker is installed: `docker --version`
2. Clone the repository
3. Run `docker-compose up -d`
4. Start implementing backend models
5. Build frontend components
6. Train ML models
7. Run tests
8. Deploy to production

Happy coding! 🚀
