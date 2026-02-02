Regex Data Extraction & Secure Validation System

A secure, regex-driven data extraction system built with Python and Object-Oriented Programming (OOP).
This project extracts structured data from raw text while actively defending against malicious input such as SQL injection, XSS attacks, and path traversal attempts.

It is designed to mimic real-world, production-level input validation systems where security is as important as functionality.

Key Features
Data Extraction

The system detects and extracts:

Email addresses

URLs (HTTP/HTTPS only)

Phone numbers (local & international)

Credit card numbers (validated using Luhn Algorithm)

Time formats (12-hour & 24-hour)

Security Protection

Built-in defenses against common attacks:

SQL Injection

Cross-Site Scripting (XSS)

Path Traversal

Malicious protocols (javascript:, data:, file:)

Fake or malformed inputs

Sensitive Data Masking

To prevent data leaks:

Credit cards are masked (****-****-****-3456)

Emails are partially masked (m***@gmail.com)

Structured Output

Results are exported as a JSON file

Clean separation between:

Extracted data

Detected security threats

Summary statistics

Design Approach

Object-Oriented Programming (OOP) for maintainability and clarity

Separation of concerns:

Validation

Extraction

Threat detection

Regex combined with logical validation (not regex alone)

Inspired by real production security pipelines

Project Structure
.
├── secure_data_extractor.py
├── test_input.txt
├── valid_results_extracted.json
└── README.md

Input File (test_input.txt)

The system processes a raw text file containing mixed real-world data, including:

Customer service transcripts

URLs, emails, phone numbers

Credit card numbers

Time stamps

Security logs

Valid and invalid test cases

Simulated malicious attempts

Example content inside test_input.txt:

Customer chats

Payment records

Security warnings

Social media mentions

Injection attempts (XSS, SQL, path traversal)

This file is intentionally noisy to test real-world robustness.

How to Run
1️⃣ Requirements

Python 3.8+

No external dependencies (standard library only)

2️⃣ Run the Program
python secure_data_extractor.py

3️⃣ Output

Reads from: test_input.txt

Generates: valid_results_extracted.json

Output Format (JSON)
{
  "extracted_data": {
    "emails": ["m***@gmail.com"],
    "urls": ["https://www.techsupport.com"],
    "phones": ["(555) 987-6543"],
    "credit_cards": ["****-****-****-5678"],
    "times": ["09:45 AM"]
  },
  "security_threats": {
    "sql_injection": ["DROP TABLE users"],
    "xss_attempts": ["<script>alert('XSS')</script>"],
    "path_traversal": ["../etc/passwd"]
  },
  "summary": {
    "total_patterns_found": 12,
    "threats_detected": 5
  }
}

Validation Techniques Used
Credit Cards

Length check (13–19 digits)

Rejects all-zero cards

Luhn Algorithm validation

Emails

RFC-aware length limits

Username & domain sanity checks

Injection & script filtering

URLs

HTTPS/HTTP only

Blocks dangerous schemes

Length & content validation

Phone Numbers

Digit-only validation

Global length constraints (7–15 digits)

SQL injection prevention

Time

Valid hour/minute ranges

12h & 24h format support

Threat Detection

The system does not just block attacks — it logs them:

SQL Injection attempts

XSS payloads

Path traversal patterns

This makes it useful for:

Security audits

Log analysis

Forensics & monitoring

Real-World Use Cases

Secure log processing

Customer support transcript analysis

Input validation systems

Fraud detection preprocessing

Security monitoring pipelines

Future Improvements

HTML tag extraction

Hashtag validation

Currency amount validation

IP address extraction

Rate-limiting simulation

CLI arguments for file input
