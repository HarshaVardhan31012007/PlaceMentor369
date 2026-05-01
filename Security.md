# 🔐 Security Policy

## 📌 Supported Versions

We actively maintain and provide security updates for the latest version of **PlacementorAI**.

| Version | Supported          |
|---------|-------------------|
| Latest  | ✅ Yes            |
| Older   | ❌ No             |

---

## 🚨 Reporting a Vulnerability

We take security seriously. If you discover a vulnerability, please report it responsibly.

### 📩 How to Report

- Email: your-email@example.com  
- Subject: **[SECURITY] PlacementorAI Vulnerability Report**

### 📝 Include the Following Details

- Description of the vulnerability
- Steps to reproduce the issue
- Possible impact
- Screenshots or proof-of-concept (if applicable)

---

## ⏱️ Response Timeline

| Stage                  | Timeframe        |
|-----------------------|------------------|
| Acknowledgement       | Within 48 hours  |
| Initial Investigation | 3–5 days         |
| Fix Deployment        | Depends on severity |

---

## 🔒 Security Measures

PlacementorAI follows industry-standard practices to ensure system security:

### 🛡️ Authentication & Authorization
- JWT-based authentication
- Role-based access control (Student, Recruiter, Admin)
- Protected API routes using middleware

### 🔑 Data Protection
- Passwords are hashed (never stored in plain text)
- Sensitive data secured using environment variables
- `.env` and `node_modules` are excluded via `.gitignore`

### 🧠 AI Governance
- AI is strictly advisory
- AI cannot:
  - Access credentials
  - Perform actions (apply, shortlist, reject)
  - Store user data

### 🧩 Backend Security
- Input validation and sanitization
- Structured API responses to prevent data leaks
- MongoDB schema enforcement using Mongoose

---

## 🚫 Prohibited Actions

To maintain platform integrity:

- Unauthorized access attempts
- Role privilege escalation
- Data scraping or automated abuse
- Exploiting API endpoints

---

## 📢 Responsible Disclosure

- Do not publicly disclose vulnerabilities before they are fixed
- Give maintainers reasonable time to resolve issues
- Avoid accessing or modifying user data

---

## 🛠️ Future Improvements

We are continuously working to enhance security by:

- Adding rate limiting
- Implementing request logging & monitoring
- Integrating security headers (Helmet.js)
- Enabling HTTPS enforcement
- Conducting periodic audits

---

## 🙌 Acknowledgements

We appreciate responsible security researchers and contributors who help improve PlacementorAI.

---

**Stay secure. Build responsibly. 🚀**
