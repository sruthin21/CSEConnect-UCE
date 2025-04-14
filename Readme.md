# 📘 CSE Department Resource Portal

A full-stack application designed to streamline access to academic resources for both **students** and **professors** in the Computer Science & Engineering (CSE) department. It supports uploading, downloading, and managing subject-wise resources and enables direct communication through real-time chat.

---

## 🛠️ Functional Requirements

### 👨‍🏫 Admin / Professors
- ✅ Login / SignUp  
- ✅ View all available resources  
- ✅ Create, update, and delete resource files  
- ✅ Directly chat with students  

### 🎓 Students
- ✅ SignUp / Login  
- ✅ Download available resources  
- ✅ Directly chat with professors  

---

## 🗃️ Database Schema

### 1. 🧑‍🎓 Student

```txt
id
name
email
rollno
password
semester        // Foreign Key to Semester
branch          // enum: aiml, cse
isRegistered    // boolean
```

### 2.  Professor

```txt
id
name
email
password
department      // example: CSE, AIML
subjects        // Array of Subject IDs taught by the professor
```

### 3.  Semester

```txt
id
semesterno      // e.g. "I", "II", "III", etc.
subjects        // Array of Subject IDs in the semester
```

### 4.  Subject

```txt
iid
name
code            // unique subject code like "CS101"
documents -> []      // Array of Document IDs
professorId     // Foreign Key to Professor
semesterId      // Foreign Key to Semester
```

### 5.  Documents

```txt
id
name
description
uploadedBy      // Professor ID
fileUrl         // S3 or local storage URL
subjectId       // Foreign Key to Subject
uploadedAt
```

🔄 Relationships
📚 A Semester has a 1-to-many relationship with Subjects

📘 A Subject is taught by one Professor but a Professor can teach many Subjects

🧑‍🎓 A Student is enrolled in one Semester, but a Semester has many Students

📄 Each Document belongs to one Subject, and is uploaded by one Professor

💬 Real-time Chat allows communication between any Student and Professor



