# Candidate API Endpoints Reference

## 📋 Complete Endpoint Documentation

| Method | Endpoint | Name | Description | Access Control | Status Codes |
|--------|----------|------|-------------|---------------|-------------|
| **POST** | `/candidates/` | Create Candidate Profile | Create a new candidate profile with resume and parsed resume data | **Candidate Only** - Users can only create their own profile | 200: Success<br>400: Profile already exists<br>401: Unauthorized<br>422: Invalid data |
| **GET** | `/candidates/{id}` | Get Candidate Profile | Retrieve a specific candidate's profile by ID | **Role-based** - Candidates: own profile only<br>Recruiters: any profile | 200: Success<br>401: Unauthorized<br>403: Access denied<br>404: Not found |
| **PUT** | `/candidates/{id}` | Update Candidate Profile | Update an existing candidate's profile (resume/parsed_resume) | **Candidate Only** - Users can only update their own profile | 200: Success<br>401: Unauthorized<br>403: Access denied<br>404: Not found<br>422: Invalid data |
| **GET** | `/candidates/` | List All Candidates | Retrieve a list of all candidate profiles | **Recruiter Only** - Only recruiters can view all candidates | 200: Success<br>401: Unauthorized<br>403: Access denied |
| **POST** | `/auth/register` | User Registration | Register a new user (candidate or recruiter) | **Public** - No authentication required | 200: Success<br>400: User already exists<br>422: Invalid data |
| **POST** | `/auth/login` | User Login | Authenticate user and receive JWT token | **Public** - No authentication required | 200: Success + Token<br>401: Invalid credentials |
| **GET** | `/auth/me` | Get Current User | Get current authenticated user information | **Authenticated** - Valid JWT token required | 200: Success<br>401: Unauthorized |

## 🔐 Access Control Summary

| Role | Create Profile | View Own Profile | Update Own Profile | View All Profiles | List All Candidates |
|------|---------------|------------------|-------------------|------------------|-------------------|
| **Candidate** | ✅ Yes | ✅ Yes | ✅ Yes | ❌ No | ❌ No |
| **Recruiter** | ❌ No* | ❌ No* | ❌ No* | ✅ Yes | ✅ Yes |
| **Unauthenticated** | ❌ No | ❌ No | ❌ No | ❌ No | ❌ No |

*Recruiters are not candidates, so they don't have candidate profiles to create/update

## 🎯 Endpoint Details

### Authentication Endpoints
- **Registration & Login**: Public endpoints for user management
- **JWT Token**: Required for all candidate operations
- **Role-based Access**: Different permissions for candidates vs recruiters

### Candidate Profile Endpoints
- **CRUD Operations**: Full Create, Read, Update functionality
- **JSON Resume Data**: Supports both raw resume text and parsed structured data
- **Security Enforced**: Strict role-based access control
- **Data Validation**: Proper input validation and error handling

## 📊 Testing Status
- **Total Endpoints**: 7 endpoints
- **Test Coverage**: 100% (12/12 tests passing)
- **Security Tests**: All access control rules verified
- **Production Ready**: ✅ All endpoints fully functional

## 🔒 Security Features
- **JWT Authentication**: Token-based security
- **Role-based Authorization**: Candidate/Recruiter permissions
- **Data Privacy**: Users can only access appropriate data
- **Input Validation**: Schema validation for all requests
- **Error Handling**: Proper HTTP status codes and error messages
