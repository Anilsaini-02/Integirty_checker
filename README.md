# Integirty_checker
# Data Integrity Checker System

A comprehensive Python-based system that monitors file integrity and sends alerts when unauthorized modifications are detected.

## Features

- **File Integrity Monitoring**: Continuously monitors specified files for unauthorized changes
- **Hash-based Detection**: Uses SHA-256 hashing to detect even minor modifications
- **User Authentication**: Secure login system with authorized and unauthorized user roles
- **Email Alerts**: Automatic email notifications to authorized users when violations are detected
- **Background Monitoring**: Runs as a service to continuously check file integrity
- **Comprehensive Logging**: Detailed logs of all activities and violations
- **Interactive Interface**: Easy-to-use command-line interface

## Installation

1. Clone or download the project files
2. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Configuration

1. **Email Configuration**: Edit `config.py` to set up your email settings:
   ```python
   EMAIL_CONFIG = {
       'smtp_server': 'smtp.gmail.com',
       'smtp_port': 587,
       'sender_email': 'your_email@gmail.com',
       'sender_password': 'your_app_password',
       'authorized_users': [
           'admin1@company.com',
           'admin2@company.com'
       ]
   }
   ```

2. **Security Settings**: Update the encryption key in `config.py`:
   ```python
   SECURITY_CONFIG = {
       'encryption_key': b'your-32-byte-encryption-key-here!!'
   }
   ```

## Usage

### First Time Setup

1. Create an admin user:
   ```bash
   python main.py --create-admin --username admin --email admin@company.com --password securepassword
   ```

2. Start the application:
   ```bash
   python main.py
   ```

### Main Features

#### 1. User Management
- Create authorized and unauthorized users
- Secure authentication system
- Session management

#### 2. File Monitoring
- Add files to the monitoring system
- Automatic hash calculation and storage
- Continuous background monitoring

#### 3. Integrity Checking
- Manual integrity checks for specific files
- Automatic scheduled checks for all monitored files
- Detailed violation reporting

#### 4. Alert System
- Email notifications for integrity violations
- System status reports
- Test alert functionality

### Interactive Menu Options

When you run the application, you'll see an interactive menu with the following options:

**For Non-logged-in Users:**
- Login
- Create User
- Exit

**For Logged-in Users:**
- Add File to Monitoring
- Check File Integrity
- View Violation Logs
- Monitoring Status
- Test Alert System
- Send Status Report
- Logout

## System Architecture

### Core Components

1. **DatabaseManager** (`database.py`): Handles all database operations
2. **IntegrityChecker** (`integrity_checker.py`): Core integrity checking functionality
3. **AlertSystem** (`alert_system.py`): Email notification system
4. **UserManager** (`user_management.py`): User authentication and session management
5. **MonitoringService** (`monitoring_service.py`): Background monitoring service
6. **Main Application** (`main.py`): Interactive interface and application entry point

### Database Schema

The system uses SQLite with the following tables:
- `users`: User accounts and authorization status
- `data_files`: Monitored files and their hashes
- `integrity_logs`: Record of all integrity violations
- `user_sessions`: Active user sessions

## Security Features

- **Password Hashing**: All passwords are hashed using SHA-256
- **Session Management**: Secure session tokens with expiration
- **Authorization Levels**: Distinction between authorized and unauthorized users
- **Audit Trail**: Complete logging of all system activities
- **File Hash Verification**: Cryptographic verification of file integrity

## Monitoring Process

1. **File Registration**: Files are added to the monitoring system with their initial hash
2. **Background Scanning**: The monitoring service periodically checks all registered files
3. **Hash Comparison**: Current file hashes are compared with stored hashes
4. **Violation Detection**: Any mismatch triggers an integrity violation
5. **Alert Generation**: Authorized users are immediately notified via email
6. **Log Recording**: All violations are recorded in the database

## Example Workflow

1. **Setup**: Create admin user and configure email settings
2. **Add Files**: Login and add important files to monitoring
3. **Monitor**: System continuously monitors files in the background
4. **Detect**: When a file is modified, the system detects the change
5. **Alert**: Authorized users receive immediate email notifications
6. **Investigate**: Review logs and take appropriate action

## Customization

### Adding New Alert Methods
Extend the `AlertSystem` class to add SMS, Slack, or other notification methods.

### Custom Hash Algorithms
Modify the `calculate_file_hash` method to use different hashing algorithms.

### Enhanced User Roles
Extend the user management system to support more granular permissions.

## Troubleshooting

### Common Issues

1. **Email Alerts Not Working**:
   - Check email configuration in `config.py`
   - Ensure app passwords are used for Gmail
   - Verify SMTP settings

2. **Database Errors**:
   - Check file permissions for the database file
   - Ensure SQLite is properly installed

3. **File Monitoring Issues**:
   - Verify file paths are correct and accessible
   - Check file permissions

### Logs

Check the `integrity_checker.log` file for detailed system logs and error messages.

## Security Considerations

- Change default encryption keys before production use
- Use strong passwords for user accounts
- Regularly review and rotate email credentials
- Monitor system logs for suspicious activities
- Keep the system updated and patched

## License

This project is provided as-is for educational and security purposes. Please ensure compliance with your organization's security policies before deployment.
