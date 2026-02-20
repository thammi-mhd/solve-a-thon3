# Departmental Digital Resource & Knowledge Hub

## 🔥 Project Overview

A centralized digital platform for Srinivas Institute of Technology's department to manage, share, and access academic resources efficiently. This system addresses the problem of scattered resources across WhatsApp and emails, reducing misinformation and improving academic collaboration through an approval-based knowledge hub.

### 🎯 Problem Statement
Currently, academic resources are scattered across WhatsApp groups and emails, leading to:
- Misinformation and outdated materials
- Difficulty in finding relevant content
- Lack of centralized verification
- Poor collaboration between faculty and students

### 💡 Solution
We created a **Departmental Digital Resource & Knowledge Hub** with:
- Role-based access control (Admin, Faculty, Student)
- Approval-based content validation
- Advanced search and filtering capabilities
- Digital notice board for announcements

## 🏗️ Tech Stack

### Option 1 (Recommended for BCA - Fastest Implementation)
- **Frontend**: HTML, CSS, Bootstrap
- **Backend**: PHP
- **Database**: MySQL
- **Server**: XAMPP

### Option 2 (Modern Alternative)
- **Frontend**: React.js
- **Backend**: Node.js + Express
- **Database**: MongoDB
- **Authentication**: JWT

## 👥 User Roles

- **Admin (HOD)**: Manages approvals, oversees content, posts notices
- **Faculty**: Uploads resources (auto-approved), views all content
- **Student**: Uploads resources (pending approval), accesses approved content

## 🗄️ Database Schema

### 1. users
```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    usn VARCHAR(20) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    semester INT,
    role ENUM('admin', 'faculty', 'student') NOT NULL,
    password VARCHAR(255) NOT NULL
);
```

### 2. resources
```sql
CREATE TABLE resources (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    subject_code VARCHAR(20) NOT NULL,
    semester INT NOT NULL,
    professor VARCHAR(100),
    file_path VARCHAR(500) NOT NULL,
    file_type ENUM('pdf', 'ppt', 'pptx', 'doc', 'docx', 'jpg', 'png') NOT NULL,
    uploaded_by INT,
    status ENUM('pending', 'approved') DEFAULT 'pending',
    upload_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    download_count INT DEFAULT 0,
    FOREIGN KEY (uploaded_by) REFERENCES users(id)
);
```

### 3. notices
```sql
CREATE TABLE notices (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    posted_by INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (posted_by) REFERENCES users(id)
);
```

## 🚀 Key Features

### 🔐 Authentication & Security
- **Student Registration**: USN-based registration with duplicate prevention
- **Role-based Login**: Automatic redirection based on user role
- **Password Hashing**: Secure password storage

### 📁 Smart Repository
- **File Validation**: Only allows PDF, PPT/PPTX, DOC/DOCX, JPG/PNG
- **Organized Storage**: Files saved in `/uploads/semester/subject/` structure
- **Role-based Upload**: Faculty uploads are auto-approved, Student uploads require approval

### 🛡️ Gatekeeper System
- **Admin Review**: Dedicated page for reviewing pending uploads
- **Approval/Rejection**: One-click approve or reject functionality
- **Content Control**: Only approved resources visible to students

### 🔍 Advanced Search Filter
- **Multi-criteria Search**: Filter by Semester, Subject Code, Professor
- **Grid Display**: Clean, organized results presentation
- **Real-time Filtering**: Dynamic search results

### 📢 Digital Notice Board
- **Department Circulars**: Centralized announcement system
- **New Badge**: 24-hour "NEW" indicator for recent notices
- **Role-based Posting**: Admin and Faculty can post notices

## ⭐ Bonus Features

- **Download Counter**: Track resource popularity
- **Top Contributor Badge**: Recognize most active students
- **Dark Mode Toggle**: Enhanced user experience
- **File Preview**: PDF preview before download

## 🎤 Presentation Strategy

### 1️⃣ Problem
"Currently resources are scattered across WhatsApp & emails causing misinformation."

### 2️⃣ Solution
"We created a centralized digital resource and approval-based knowledge hub."

### 3️⃣ Key Innovation
"Our Gatekeeper approval logic prevents spam and ensures verified academic materials."

### 4️⃣ Impact
- Reduces misinformation
- Centralized system
- Improves academic collaboration

## ⏳ 24-Hour Development Plan

- **Hour 1-2**: Database setup + Authentication system
- **Hour 3-6**: File upload + Role-based logic
- **Hour 7-10**: Approval system implementation
- **Hour 11-14**: Search filter functionality
- **Hour 15-18**: Notice board development
- **Hour 19-21**: UI polish and responsive design
- **Hour 22-24**: Testing, debugging, and presentation preparation

## 🛠️ Installation & Setup

### Prerequisites
- XAMPP (Apache, MySQL, PHP)
- Web browser

### Setup Steps
1. Clone the repository
2. Start XAMPP and ensure Apache & MySQL are running
3. Import the database schema from `database/schema.sql`
4. Copy files to `htdocs` directory
5. Configure database connection in `config/database.php`
6. Access via `http://localhost/project-directory`

### Default Admin Credentials
- USN: ADMIN001
- Password: admin123

## 📱 Usage

### For Students
1. Register with USN, Name, Semester
2. Login to access approved resources
3. Use filters to find specific materials
4. Download resources and view notices

### For Faculty
1. Login with faculty credentials
2. Upload resources (auto-approved)
3. View all department resources
4. Access notice board

### For Admin (HOD)
1. Login to admin dashboard
2. Review and approve/reject student uploads
3. Post department notices
4. Monitor system usage

## 🤝 Contributing

This is a hackathon project. For contributions:
1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

## 📄 License

This project is developed for educational purposes as part of a hackathon.

## 👥 Team

- **Tech Stack Decision**: PHP/MySQL (recommended for speed)
- **Team Size**: Individual/Small team (2-3 members optimal)

---

**Ready to build a winning solution! 🔥🚀**

*Built with ❤️ for Srinivas Institute of Technology*