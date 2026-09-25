# Service Blueprint - Task Manager Web Service

## 1. Service Overview
App: To-Do Web App (React + Node + MongoDB)
Users: 100-500 daily
Cloud: AWS

Flow: User -> CloudFront -> ALB -> EC2 Docker -> MongoDB

## 2. Operational Contract
Frontend: React - UI
Backend: Node.js - API /health endpoint
DB: MongoDB Atlas
Logs: CloudWatch JSON logs
Owner: DevOps Team

Runbook: If health fails -> Restart container

## 3. SLOs & SLIs
SLO 1 Availability 99.9% (43 min downtime/month)
SLI: success_req / total_req * 100

SLO 2 Latency p95 < 300ms, p99 < 500ms
SLI: duration histogram at GET /api/tasks

SLO 3 Error Rate < 0.5% 5xx
SLI: 5xx / total

Error Budget: 0.1% - Budget burn aana deploy stop

## 4. Cloud Cost Envelope - Monthly
EC2 t3.micro - $8.50
ALB - $16.20
S3 10GB - $0.50
CloudFront 50GB - $4.25
MongoDB M0 Free - $0.00
CloudWatch - $3.00
Total = $32.95/month

Budget Alert at 80% = $26
Optimization: Dev server auto-off at night

## 5. Ready Checklist
[ ] Dockerfile ready
[ ] /health 200 OK
[ ] ENV vars only, no secrets in code
[ ] Cost < $35 verified

4. Commit changes click pannu
5. Commit message: Add Service Blueprint with SLOs and Cost Envelope
6. Commit panni mudichidu da!
