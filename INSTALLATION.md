# Clinic Management System - Installation Guide

## System Requirements

### Minimum Hardware Requirements
- 4GB RAM (8GB recommended)
- 2GB free disk space
- 1024x768 screen resolution

### Software Requirements
- Python 3.9 or higher
- Git
- wkhtmltopdf (for PDF generation)
- Web browser (Chrome/Firefox/Edge recommended)

## Installation Steps

### 1. Python Installation

#### Windows:
1. Download Python 3.9+ from [python.org](https://python.org)
2. Run installer, ensure you:
   - ✅ Check "Add Python to PATH"
   - ✅ Check "Install pip"
3. Verify installation:
   ```bash
   python --version
   pip --version
   ```

#### Linux (Ubuntu/Debian):
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

#### macOS:
```bash
# Using Homebrew
brew install python
```

### 2. Install wkhtmltopdf

#### Windows:
1. Download from [wkhtmltopdf.org](https://wkhtmltopdf.org/downloads.html)
2. Run installer
3. Add to PATH:
   - Open System Properties (Win + Pause|Break)
   - Advanced system settings → Environment Variables
   - Under "System Variables", edit "Path"
   - Add: `C:\Program Files\wkhtmltopdf\bin`

#### Linux:
```bash
sudo apt-get install wkhtmltopdf
```

#### macOS:
```bash
brew install wkhtmltopdf
```

### 3. Clone & Setup Application

1. Clone repository:
```bash
git clone https://github.com/yourusername/clinic-management.git
cd clinic-management
```

2. Create virtual environment:
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/macOS
python3 -m venv venv
source venv/bin/activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

### 4. Database Setup

1. Initialize database:
```bash
flask db upgrade
```

2. Create admin user:
```bash
python create_admin.py
```

Default admin credentials:
- Email: admin@gmail.com
- Password: admin@123

### 5. Configuration

1. Create `.env` file in root directory:
```env
FLASK_APP=run.py
FLASK_ENV=development
SECRET_KEY=your-secret-key-here
DATABASE_URL=sqlite:///clinic.db

# Email Configuration (Optional)
MAIL_SERVER=smtp.gmail.com
MAIL_PORT=587
MAIL_USE_TLS=True
MAIL_USERNAME=your-email@gmail.com
MAIL_PASSWORD=your-app-password
```

### 6. Running the Application

1. Start the server:
```bash
# Windows
python run.py

# Linux/macOS
python3 run.py
```

2. Access the application:
- Open browser and navigate to: `http://localhost:5000`
- Login with admin credentials

### 7. Creating Desktop Shortcut (Optional)

#### Windows:
1. Install pyinstaller:
```bash
pip install pyinstaller
```

2. Create executable:
```bash
pyinstaller --onefile --icon=app/static/images/icon.ico --name ClinicApp run.py
```

3. Find executable in `dist` folder
4. Create shortcut on desktop

#### Linux:
1. Create .desktop file:
```bash
[Desktop Entry]
Name=Clinic Management
Exec=/path/to/venv/bin/python /path/to/run.py
Icon=/path/to/icon.png
Type=Application
Categories=Office;
```

## Common Issues & Solutions

### Database Errors
- **Issue**: "No such table" error
  - **Solution**: Run `flask db upgrade`

### PDF Generation Errors
- **Issue**: "wkhtmltopdf not found"
  - **Solution**: Verify PATH settings and installation

### Email Errors
- **Issue**: Gmail authentication failed
  - **Solution**: Enable "Less secure app access" or use App Password

## Updating the Application

1. Pull latest changes:
```bash
git pull origin main
```

2. Update dependencies:
```bash
pip install -r requirements.txt
```

3. Update database:
```bash
flask db upgrade
```

## Security Recommendations

1. Change default admin password after first login
2. Use strong SECRET_KEY in .env file
3. Configure email settings for notifications
4. Regular backups of the database file
5. Keep Python and all dependencies updated

## Support

For issues and support:
1. Check common issues section above
2. Visit our documentation: [docs link]
3. Create issue on GitHub: [issues link]
4. Contact support: support@example.com

## Backup & Recovery

### Database Backup
```bash
# Windows
copy clinic.db clinic.db.backup

# Linux/macOS
cp clinic.db clinic.db.backup
```

### Restore from Backup
```bash
# Windows
copy clinic.db.backup clinic.db

# Linux/macOS
cp clinic.db.backup clinic.db
```

## Uninstallation

1. Stop the application
2. Delete the application directory
3. (Optional) Remove Python and dependencies

---

Last Updated: March 2024
Version: 1.0.0