# Cryptonic_Virtual_internship_project1
## Secure Web Application – Security Design Documentation
📌 Project Title

Secure Notes Web Application with Threat Hardening

## Project Goal

The objective of this project is to demonstrate how to build a secure web application by implementing real-world cybersecurity practices instead of just finding vulnerabilities.

This project focuses on defensive security engineering.

## Tech Stack
Component	Technology
Backend	Python Flask
Database	SQLite
Frontend	HTML + CSS
Security	Werkzeug hashing, sessions, validation

##Security Architecture Overview

The application allows users to:

Register

Login securely

Create private notes

Access only their own data

Security is implemented at multiple layers to ensure protection against common web threats.

## Security Measures Implemented
1️⃣ Authentication & Authorization

Goal: Ensure only verified users access protected resources.

Implemented

User login system with sessions

Each session stores user_id

Protected routes check session existence

Users cannot access dashboard without login

if "user_id" not in session:
    return redirect("/login")

Risk Mitigated

Unauthorized access

Direct URL access to private pages

## Password Security (Hashing)

Passwords are never stored in plain text.

generate_password_hash(password)
check_password_hash(hash, password)

Algorithm Used

Werkzeug PBKDF2 hashing

Risk Mitigated

Database breach exposure

Credential theft

## Password Policy Enforcement

User passwords must contain:

Minimum 8 characters

At least one number

At least one special character

Risk Mitigated

Weak password attacks

Brute force success probability

## SQL Injection Prevention

All database queries use parameterized statements:

cursor.execute("SELECT * FROM users WHERE username = ?", (username,))

Risk Mitigated

SQL Injection

Data leakage

Database compromise

## Session Management

Sessions are created only after login

Session cleared on logout

Dashboard access controlled by session

session.clear()

Risk Mitigated

Session misuse

Unauthorized session reuse

## Input Validation

User inputs are validated for:

Length

Format

Prevents malicious payloads from being processed.

Risk Mitigated

Injection attacks

Buffer abuse

## Access Control

Each note is linked to a specific user ID:

SELECT content FROM notes WHERE user_id = ?


Users cannot see others' data.

Risk Mitigated

Horizontal privilege escalation

 ##Threat vs Defense Summary
Threat	Defense Used
Password theft	Hashing
SQL Injection	Parameterized queries
Unauthorized access	Session authentication
Weak passwords	Password policy
Session hijacking	Controlled sessions
Data exposure	User-based access control

##Future Security Improvements (Advanced Hardening)

CSRF protection

Rate limiting login attempts

Account lock after failed attempts

📷
##Screenshots







<img width="400" height="400" alt="Screenshot 2026-02-08 200211" src="https://github.com/user-attachments/assets/9c05652a-f9b0-46c4-9dac-96e07a6ab726" />






<img width="400" height="400" alt="Screenshot 2026-02-08 200226" src="https://github.com/user-attachments/assets/3b3890fe-b995-40a1-adbb-9b7bbf2e3db7" />


