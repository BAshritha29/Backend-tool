# Internship Management System

A comprehensive web application for managing internship applications and certificate verification, built with React, Node.js, Express, and Google Sheets integration.

## Features

### 🚀 Core Functionality
- **Application Management**: Complete internship application form with validation
- **Certificate Verification**: Verify certificates using unique IDs
- **Dashboard**: Admin panel for managing applications and tracking progress
- **Google Sheets Integration**: Automatic data storage and backup
- **File Upload**: Resume upload with validation and security
- **Real-time Validation**: Form validation with immediate feedback

### 🎨 Design Features
- **Modern UI**: Beautiful, responsive design with Tailwind CSS
- **Animations**: Smooth transitions and micro-interactions
- **Mobile-First**: Optimized for all device sizes
- **Professional Styling**: Apple-level design aesthetics
- **Accessible**: WCAG compliant with proper contrast ratios

### 🔧 Technical Features
- **RESTful API**: Well-structured backend with proper error handling
- **Input Validation**: Server-side validation using Joi
- **File Management**: Secure file upload with type validation
- **Mock Data**: Sample data for testing and development
- **Error Handling**: Comprehensive error management
- **Environment Configuration**: Flexible configuration system

## Quick Start

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn
- Google Cloud Platform account (for Sheets integration)

### Installation

1. **Clone and install dependencies**
   ```bash
   npm install
   ```

2. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Create uploads directory**
   ```bash
   mkdir uploads
   ```

4. **Start the development servers**
   ```bash
   # Terminal 1: Start the frontend
   npm run dev

   # Terminal 2: Start the backend
   npm run server
   ```

5. **Access the application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:3001

## Google Sheets Integration

### Setup Steps

1. **Create a Google Cloud Project**
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project or select existing one

2. **Enable Google Sheets API**
   - Navigate to APIs & Services > Library
   - Search for "Google Sheets API" and enable it

3. **Create Service Account**
   - Go to APIs & Services > Credentials
   - Click "Create Credentials" > "Service Account"
   - Download the JSON key file

4. **Configure Spreadsheet**
   - Create a new Google Sheets document
   - Share it with the service account email
   - Copy the spreadsheet ID from the URL

5. **Update Environment Variables**
   ```bash
   GOOGLE_SHEETS_ID=your-spreadsheet-id
   GOOGLE_SHEETS_CLIENT_EMAIL=service-account@project.iam.gserviceaccount.com
   GOOGLE_SHEETS_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
   ```

## API Documentation

### Applications Endpoints

#### GET /api/applications
Get all applications
```bash
curl http://localhost:3001/api/applications
```

#### POST /api/applications
Submit new application (with file upload)
```bash
curl -X POST http://localhost:3001/api/applications \
  -F "fullName=John Doe" \
  -F "email=john@example.com" \
  -F "resume=@path/to/resume.pdf"
```

#### PATCH /api/applications/:id
Update application status
```bash
curl -X PATCH http://localhost:3001/api/applications/app-001 \
  -H "Content-Type: application/json" \
  -d '{"status": "accepted"}'
```

### Certificates Endpoints

#### GET /api/certificates/:id
Verify certificate by ID
```bash
curl http://localhost:3001/api/certificates/CERT-2024-001
```

#### POST /api/certificates
Issue new certificate
```bash
curl -X POST http://localhost:3001/api/certificates \
  -H "Content-Type: application/json" \
  -d '{
    "studentName": "John Doe",
    "college": "MIT",
    "domain": "Web Development",
    "duration": "3 Months",
    "startDate": "2024-01-15",
    "endDate": "2024-04-15"
  }'
```

## Testing

### Sample Certificate IDs
- `CERT-2024-001` - John Doe (Web Development)
- `CERT-2024-002` - Jane Smith (Data Science)
- `CERT-2024-003` - Alex Rodriguez (Mobile Development)

### Testing the Application

1. **Submit Application**
   - Navigate to "Apply for Internship"
   - Fill out the form with valid data
   - Upload a resume (PDF/DOC/DOCX)
   - Submit and verify success message

2. **Verify Certificate**
   - Go to "Verify Certificate"
   - Enter sample certificate ID: `CERT-2024-001`
   - Verify certificate details display

3. **Check Dashboard**
   - Visit "Dashboard" tab
   - View application statistics
   - Test filtering and search functionality

## Project Structure

```
├── src/
│   ├── components/
│   │   ├── ApplicationForm.tsx
│   │   ├── CertificateVerification.tsx
│   │   └── Dashboard.tsx
│   ├── App.tsx
│   └── main.tsx
├── server/
│   ├── routes/
│   │   ├── applications.js
│   │   └── certificates.js
│   └── index.js
├── uploads/          # File upload directory
├── package.json
└── README.md
```

## Security Features

- **Input Validation**: Server-side validation for all inputs
- **File Type Validation**: Restricted file uploads (PDF, DOC, DOCX only)
- **File Size Limits**: Maximum 10MB file uploads
- **CORS Configuration**: Proper cross-origin resource sharing
- **Error Handling**: Secure error messages without data leaks

## Deployment

### Frontend Deployment
```bash
npm run build
# Deploy the dist/ folder to your hosting provider
```

### Backend Deployment
1. Set up production environment variables
2. Configure file upload directory
3. Set up Google Sheets access
4. Deploy to your preferred hosting platform

### Environment Variables for Production
```bash
NODE_ENV=production
PORT=3001
GOOGLE_SHEETS_ID=your-production-spreadsheet-id
GOOGLE_SHEETS_CLIENT_EMAIL=your-production-service-account
GOOGLE_SHEETS_PRIVATE_KEY=your-production-private-key
```

## Support

For issues or questions:
1. Check the console for error messages
2. Verify environment variables are set correctly
3. Ensure Google Sheets permissions are configured
4. Check file upload directory permissions

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

---

Built with ❤️ using React, Node.js, Express, and Google Sheets API