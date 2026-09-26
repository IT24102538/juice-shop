# IE3142 DevSecOps - OWASP Juice Shop Pipeline

## Module: IE3142 DevOps Security | Year 3 Semester 1 2026

## Overview

This repository demonstrates a complete DevSecOps pipeline built around
[OWASP Juice Shop](https://owasp.org/www-project-juice-shop/), an intentionally
vulnerable Node.js/Angular web application.

### Application Architecture

```
[User Browser]
    |  HTTP/HTTPS
    v
[Nginx Reverse Proxy :80]
    |  Internal HTTP
    v
[OWASP Juice Shop :3000]
(Angular SPA + Node.js Express API)
    |  SQLite File I/O
    v
[SQLite Database]
```

## Security Vulnerabilities Addressed

| # | Vulnerability | CWE | OWASP Category | Status |
|---|--------------|-----|----------------|--------|
| 1 | DOM-Based XSS | CWE-79 | A03:2021 Injection | Fixed |
| 2 | SQL Injection | CWE-89 | A03:2021 Injection | Fixed |
| 3 | Weak JWT Secret | CWE-347 | A07:2021 Auth Failures | Fixed |
| 4 | Broken Access Control (BOLA) | CWE-284 | A01:2021 Access Control | Fixed |

## CI/CD Security Gates

| Gate | Tool | Triggers Failure On |
|------|------|-------------------|
| SAST | Semgrep | ERROR severity findings |
| Dependency | npm audit | HIGH vulnerabilities |
| Secrets | Gitleaks | Committed credentials |
| Container | Trivy | CRITICAL/HIGH CVEs |
| DAST (Extra) | OWASP ZAP | Baseline passive scan |

## Setup & Run Instructions

### Prerequisites
- Docker Desktop installed and running
- Git installed

### Quick Start

```bash
# Clone the repository
git clone https://github.com/IT24102538/juice-shop-devsecops.git
cd juice-shop-devsecops

# Create .env file with secrets (never commit this file)
echo "JWT_SECRET=ToZtusung+VuNEzc/sv+0j/Mf7KaZsGjkbcZqsRRyTTt+sFctU3goa/XooJV+ypL" > .env

# Start all services
docker-compose up -d

# Access the application
# Juice Shop: http://localhost:3000
# Via Nginx:  http://localhost:80
```

### Verify Running
```bash
docker-compose ps
```

### Stop Services
```bash
docker-compose down
```

## Group Members

| Member | Student ID |
|--------|-----------|
| Sithum Sanjana | IT24102538 | 
| U.Ayushyaa | IT24102996 | 
| Sherangi S.A.G.A| IT24100958 | 
| Manukulasuriya R.N | IT24100792 | 

## References

- OWASP Juice Shop: https://owasp.org/www-project-juice-shop/
- OWASP Top Ten 2021: https://owasp.org/Top10/