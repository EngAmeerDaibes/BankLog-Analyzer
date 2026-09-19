# BankLog-Analyzer
A command-line log analysis and monitoring tool built with Bash to detect security events, analyze banking transactions, track user sessions, and summarize server activity.

A Bash-based banking server log analyzer that transforms raw server logs into structured, human-readable reports for security monitoring, transaction analysis, session tracking, query inspection, and system activity summaries.

*************Overview*************

Banking database servers generate large amounts of log data containing authentication attempts, database queries, financial transactions, backups, and system errors. Manually reviewing these logs can be slow and impractical.

BankLog Sentinel is a shell scripting project that automatically parses a bank database server log file and extracts useful information through a menu-driven command-line interface.

*************Features*************

The project provides the following analysis services:

Failed Login Report

Counts failed login attempts.

Groups failed attempts by client IP address.

Groups failed attempts by username.

Flags IP addresses with 3 or more failed attempts as possible brute-force sources.

Query Activity Summary

Counts all database query events.

Breaks queries down by type:

SELECT

INSERT

UPDATE

DELETE

Slow Query Detector

Extracts warning entries related to slow queries.

Displays execution time.

Shows the user responsible for each slow query.

Transaction Report

Counts deposits.

Counts withdrawals.

Counts declined transactions.

Counts rollbacks.

Calculates total deposited and withdrawn amounts when available.

Critical Events Report

Displays all CRITICAL log entries.

Includes timestamps to help administrators investigate severe failures quickly.

User Activity Report

Accepts a username as input.

Displays all actions performed by that user.

Sorts the activity chronologically.

Login/Logout Session Report

Lists all sessions.

Displays login time.

Displays logout time when available.

Calculates session duration.

Events-per-Hour Report

Counts the number of log events that occurred during each hour.

Helps identify peak system usage times.

General Log Summary

Displays the total number of log entries.

Counts events by log level:

INFO

WARNING

ERROR

CRITICAL

Identifies the busiest module.

Log File Format

The analyzer expects log entries in the following format:

[TIMESTAMP] [LOG_LEVEL] [SESSION_ID] [USER] [CLIENT_IP] [MODULE] - MESSAGE

*************Example:

[2026-08-15 08:07:33] [ERROR] [SESSION_1003] [unknown] [203.0.113.55] [AUTH] - Failed login attempt for user root (invalid password)

Fields

Field

Description

TIMESTAMP

Date and time when the event was logged

LOG_LEVEL

Severity level: INFO, WARNING, ERROR, or CRITICAL

SESSION_ID

Unique session identifier such as SESSION_1003

USER

Username associated with the event

CLIENT_IP

IPv4 address where the request originated

MODULE

System module such as AUTH, QUERY, TRANSACTION, or BACKUP

MESSAGE

Human-readable description of the event

Log Levels

INFO — Normal system operations such as successful logins, completed queries, and backups.

WARNING — Non-fatal issues requiring attention, such as slow queries or declined transactions.

ERROR — Failed operations such as failed login attempts or failed transactions.

CRITICAL — Severe failures such as backup failures or transaction rollbacks caused by system errors.

*************Modules*************

AUTH — Login and logout activity.

QUERY — Database queries.

TRANSACTION — Deposits, withdrawals, declined operations, and rollbacks.

BACKUP — Database backup activity.

Technologies Used

Bash / Shell Scripting

Linux / Unix command-line tools

grep

awk

sed

cut

sort

uniq

wc

date

*************Project Structure*************

A typical repository structure can look like this:

BankLog-Sentinel/
├── README.md
├── bank_loganalyzer.sh
└── bank_server.log

bank_loganalyzer.sh — Main shell script.

bank_server.log — Sample log file used for testing.

README.md — Project documentation.

Requirements

To run the project, you need a Linux or Unix-like environment with Bash and standard command-line utilities installed.

You can verify Bash with:

bash --version

Running the Project

Clone the repository:

git clone <repository-url>

Enter the project directory:

cd BankLog-Sentinel

Give the script execute permission:

chmod +x bank_loganalyzer.sh

Run the script:

./bank_loganalyzer.sh

If your implementation accepts the log file as an argument, run it according to your script's expected syntax.

Menu-Driven Interface

The script is designed around a menu that allows the user to select an individual analysis service or generate a complete report.

Example menu:

==========================================
        BANK SERVER LOG ANALYZER
==========================================

1. Failed Login Report
2. Query Activity Summary
3. Slow Query Detector
4. Transaction Report
5. Critical Events Report
6. User Activity Report
7. Login/Logout Session Report
8. Events-per-Hour Report
9. General Log Summary
10. Run All Reports
0. Exit

*************Error Handling*************

The project is designed to handle common input problems gracefully, including:

Missing log files.

Invalid file paths.

Invalid menu selections.

Usernames that do not exist in the log.

Invalid or missing input.

*************Design*************

The project follows a modular structure. Each analysis service is implemented as a separate function, while shared operations such as file validation and field processing can be placed in reusable helper functions.

This makes the script easier to read, test, maintain, and extend.

Learning Objectives

This project demonstrates practical use of:

Shell scripting functions.

Loops and conditionals.

Text processing.

String manipulation.

Unix/Linux pipelines.

Log parsing.

Data aggregation.

Input validation.

Error handling.

Modular program design.
