# APNA - AI-Powered Job Platform

A comprehensive job matching platform built with Django and React that uses AI-powered resume analysis and intelligent job matching to connect candidates with recruiters.

## Live Demo

**[🔗 View Live Demo](https://apna-two.vercel.app/)**

Experience the full functionality of APNA job platform with our live deployment on Vercel.

## Features

### For Candidates
- **Secure Authentication** - Registration, login, and password reset with JWT tokens
- **AI-Powered Resume Analysis** - Upload resumes for automatic skill extraction using Google Gemini AI
- **Intelligent Profile Verification** - AI-generated scenario-based questions for profile verification
- **Smart Job Matching** - Get personalized job recommendations based on extracted skills
- **Interactive Job Applications** - Take custom tests created by HR teams
- **Application Tracking** - Monitor application status and view applied jobs
- **Responsive Dashboard** - Mobile-friendly interface for job management

### For HR/Recruiters
- **Comprehensive Job Posting** - Create detailed job listings with custom requirements
- **Custom Assessment Creation** - Design scenario-based questions for candidate evaluation
- **Candidate Management** - View and evaluate applicant profiles and test results
- **Advanced Filtering** - Search and filter candidates based on various criteria
- **Application Analytics** - Track application metrics and candidate performance
- **Resume Viewer** - Access detailed candidate profiles and uploaded resumes

### AI-Powered Features
- **Resume Text Extraction** - Support for PDF resumes with OCR fallback using Tesseract
- **Skill Identification** - Automatic extraction of technical and soft skills
- **Experience Analysis** - Work history and project identification
- **Question Generation** - AI-generated interview questions based on candidate profile
- **Intelligent Matching** - Algorithm-based job-candidate matching system

## Architecture & Technology Stack

### Backend
- **Framework**: Django 5.1.6 with Django REST Framework
- **Database**: MongoDB with PyMongo
- **Authentication**: JWT (PyJWT) with bcrypt encryption
- **AI Integration**: Google Generative AI (Gemini)
- **File Processing**: PyMuPDF for PDF parsing, Tesseract OCR for text extraction
- **Image Processing**: Pillow for image manipulation
- **CORS**: django-cors-headers for cross-origin requests

### Frontend
- **Framework**: React 19.0.0 with Create React App
- **Routing**: React Router DOM 7.1.5
- **Styling**: TailwindCSS 3.2.4 with responsive design
- **State Management**: React Hooks (useState, useEffect)
- **HTTP Client**: Fetch API with cookie-based authentication
- **UI Components**: React Icons, React Toastify for notifications
- **Cookie Management**: js-cookie for token storage

### Development Tools
- **Package Managers**: npm (Frontend), pip (Backend)
- **Bundling**: Webpack (via Create React App)
- **PostCSS**: Autoprefixer and TailwindCSS processing
- **Build Tools**: Django Extensions, Gunicorn for production

## Project Structure

```
APNA/
├── Backend/                    # Django Backend Application
│   ├── manage.py              # Django management script
│   ├── requirements.txt       # Python dependencies
│   ├── db.sqlite3            # SQLite database (development)
│   ├── backend/              # Main Django project configuration
│   │   ├── settings.py       # Django settings and CORS configuration
│   │   ├── urls.py           # Main URL routing
│   │   ├── wsgi.py           # WSGI configuration
│   │   └── asgi.py           # ASGI configuration
│   ├── apna/                 # Main Django application
│   │   ├── models.py         # Database models (using MongoDB)
│   │   ├── candidate_views.py # Candidate-related API endpoints
│   │   ├── hr_views.py       # HR-related API endpoints
│   │   ├── urls.py           # Application URL patterns
│   │   ├── admin.py          # Django admin configuration
│   │   └── migrations/       # Database migrations
│   └── uploads/              # Resume file storage
│       ├── user@email.com/   # User-specific upload directories
│       └── ...
├── Frontend/                  # React Frontend Application
│   ├── package.json          # NPM dependencies and scripts
│   ├── tailwind.config.js    # TailwindCSS configuration
│   ├── postcss.config.js     # PostCSS configuration
│   ├── public/               # Static assets
│   │   ├── index.html        # Main HTML template
│   │   ├── favicon.ico       # Application icon
│   │   └── manifest.json     # PWA manifest
│   └── src/                  # React source code
│       ├── App.js            # Main application component with routing
│       ├── index.js          # React entry point
│       ├── components/       # Reusable UI components
│       │   ├── HrNavbar.js           # HR navigation component
│       │   ├── ApplicantNavbar.js    # Candidate navigation component
│       │   └── PasswordStrengthBar.js # Password validation component
│       └── pages/            # Page components
│           ├── Landing.js            # Homepage
│           ├── Candidate/            # Candidate-specific pages
│           │   ├── CandidateLogin.js
│           │   ├── CandidateRegister.js
│           │   ├── CandidateDashboard.js
│           │   ├── CandidateProfile.js
│           │   ├── CandidateResumeUpload.js
│           │   ├── Jobs.js
│           │   ├── JobsForYou.js
│           │   └── JobPreview.js
│           └── HR/                   # HR-specific pages
│               ├── Login.js
│               ├── Register.js
│               ├── HrDashboard.js
│               ├── HRProfile.js
│               ├── PostJob.js
│               └── CandidateDetails.js
└── README.md                 # Project documentation
```

## Installation & Setup

### Prerequisites
- Python 3.8+ with pip
- Node.js 14+ with npm
- MongoDB Atlas account or local MongoDB installation
- Google AI API key (for Gemini integration)
- Tesseract OCR (for resume text extraction)

### Backend Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Hariharanpugazh/APNA.git
   cd APNA/Backend
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # Linux/Mac
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Install Tesseract OCR**
   - **Windows**: Download from [GitHub Tesseract](https://github.com/UB-Mannheim/tesseract/wiki)
   - **Linux**: `sudo apt-get install tesseract-ocr`
   - **Mac**: `brew install tesseract`

5. **Configure environment variables**
   Update `backend/settings.py` with your MongoDB connection string and Google AI API key in `candidate_views.py`

6. **Run the development server**
   ```bash
   python manage.py runserver
   ```

   The backend will be available at `http://localhost:8000`

### Frontend Setup

1. **Navigate to frontend directory**
   ```bash
   cd ../Frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm start
   ```

   The frontend will be available at `http://localhost:3000`

## Configuration

### Database Configuration
The application uses MongoDB for data storage. Update the connection string in both view files:
```python
client = MongoClient('mongodb+srv://username:password@cluster.mongodb.net/')
```

### AI Integration Setup
Configure Google Gemini AI in `candidate_views.py`:
```python
genai.configure(api_key="your-google-ai-api-key")
```

### CORS Configuration
The backend is configured to allow requests from the React frontend. Update `CORS_TRUSTED_ORIGINS` in `settings.py` if needed.

## Database Schema

### Collections in MongoDB

#### `candidate` Collection
```javascript
{
  _id: ObjectId,
  name: String,
  email: String,
  password: String (hashed),
  otp: Number,
  otp_expiry: DateTime,
  resume_skills: [String],
  work_experience: [String],
  projects: [String],
  generated_questions: [{
    question: String,
    keyword: String/Array
  }],
  profile_status: String // "Pending" | "Verified"
}
```

#### `hr` Collection
```javascript
{
  _id: ObjectId,
  name: String,
  email: String,
  password: String (hashed),
  otp: Number,
  otp_expiry: DateTime
}
```

#### `job_details` Collection
```javascript
{
  _id: ObjectId,
  hr_id: ObjectId,
  job_title: String,
  company_name: String,
  job_description: String,
  contact_email: String,
  application_deadline: String,
  work_type: String,
  job_location: String,
  category: String,
  skills_required: String/Array,
  salary: Number,
  experience: Number,
  pass_percentage: Number,
  hr_questions: [{
    question: String,
    keyword: String/Array
  }],
  selected_candidates: [Object],
  applied_candidates: [Object]
}
```

## API Endpoints

### Authentication Endpoints

#### Candidate Authentication
- `POST /apna/register/` - Candidate registration
- `POST /apna/login/` - Candidate login
- `POST /apna/forgot-password/` - Password reset request
- `POST /apna/reset-password/` - Password reset confirmation

#### HR Authentication
- `POST /apna/hr_register/` - HR registration
- `POST /apna/hr_login/` - HR login
- `POST /apna/hr_forgot-password/` - HR password reset request
- `POST /apna/hr_reset-password/` - HR password reset confirmation

### Candidate Endpoints
- `GET /apna/candidate_profile/` - Get candidate profile
- `GET /apna/get_all_jobs/` - Fetch all available jobs
- `GET /apna/get_job_details/<job_id>/` - Get specific job details
- `POST /apna/apply_job/` - Apply for a job with test submission
- `GET /apna/check_application_status/<job_id>/` - Check application status
- `GET /apna/get_applied_jobs/` - Get candidate's applied jobs
- `POST /apna/upload_resume/` - Upload and analyze resume
- `POST /apna/candidate_test/` - Submit profile verification test
- `GET /apna/get_matched_jobs/` - Get AI-matched job recommendations

### HR Endpoints
- `GET /apna/get_hr_profile/` - Get HR profile
- `POST /apna/post_job/` - Create new job posting
- `GET /apna/get_jobs/` - Get HR's posted jobs
- `GET /apna/get_selected_candidates/<job_id>/` - Get candidates for a job
- `GET /apna/candidate/<email>` - Get specific candidate details
- `DELETE /apna/delete_job/<job_id>/` - Delete job posting

## Testing

### Running Backend Tests
```bash
cd Backend
python manage.py test
```

### Running Frontend Tests
```bash
cd Frontend
npm test
```

## Deployment

### Backend Deployment (Using Gunicorn)
```bash
pip install gunicorn
gunicorn backend.wsgi:application --bind 0.0.0.0:8000
```

### Frontend Deployment
```bash
npm run build
# Serve the build folder using a web server
```

### Environment Variables for Production
- Set `DEBUG = False` in Django settings
- Configure proper `ALLOWED_HOSTS`
- Use environment variables for sensitive data
- Set up proper CORS origins
- Configure MongoDB with authentication

## Security Features

- **Password Hashing**: bcrypt encryption for all passwords
- **JWT Authentication**: Secure token-based authentication
- **CORS Protection**: Configured cross-origin request handling
- **Input Validation**: Server-side validation for all inputs
- **File Upload Security**: Restricted file types and size limits
- **SQL Injection Prevention**: MongoDB parameterized queries

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


## Team

- **Developer**: Hariharan Pugazh , [Kavin-Bakyaraj](https://github.com/Kavin-Bakyaraj) 
- **Repository**: [GitHub - APNA](https://github.com/Hariharanpugazh/APNA)

## Known Issues

- Resume OCR processing may require Tesseract path configuration on Windows
- Large PDF files may take longer to process
- MongoDB connection needs proper network access configuration

## Future Enhancements

- [ ] Real-time chat between candidates and HR
- [ ] Video interview integration
- [ ] Advanced analytics dashboard
- [ ] Mobile application development
- [ ] Integration with LinkedIn and other job platforms
- [ ] Machine learning model improvements
- [ ] Multi-language support
- [ ] Email notification system
- [ ] Calendar integration for interviews

## Support

For support and questions, please create an issue in the GitHub repository or contact the development team.

---

**Built with ♥ using Django, React, and AI technologies**
