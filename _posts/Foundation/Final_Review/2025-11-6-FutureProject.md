---
layout: post
title:  Future Project Issue 
description: Future Plans
categories: ['Collaboration']
permalink: /FutureProject
date: 2025-10-21
---
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>EduTrack — Project Outline</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--muted:#9aa6b2;--accent:#60a5fa;--glass: rgba(255,255,255,0.03)}
    html,body{height:100%;margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial}
    body{background:linear-gradient(180deg,#071124 0%, #071a2a 100%);color:#e6eef6;padding:40px 20px}
    .container{max-width:900px;margin:0 auto;background:linear-gradient(180deg,var(--card), #06101a);border-radius:14px;padding:40px;box-shadow:0 6px 28px rgba(2,6,23,0.6)}
    h1{font-size:32px;margin:0 0 10px;color:#e6eef6}
    h2{font-size:20px;margin:32px 0 16px;color:#60a5fa;border-bottom:2px solid rgba(96,165,250,0.2);padding-bottom:8px}
    h3{font-size:16px;margin:20px 0 12px;color:#8ab4f8}
    p{color:var(--muted);line-height:1.6;margin:12px 0}
    .badge{display:inline-block;background:var(--glass);padding:8px 14px;border-radius:999px;font-size:13px;color:var(--accent);margin-bottom:16px;border:1px solid rgba(96,165,250,0.2)}
    .list{margin:12px 0;padding-left:24px}
    .list li{margin:10px 0;line-height:1.5}
    .list li strong{color:#e6eef6}
    .entity-box{background:rgba(255,255,255,0.02);border-left:3px solid var(--accent);padding:16px;margin:12px 0;border-radius:6px}
    .entity-box h3{margin-top:0}
    footer{font-size:13px;color:var(--muted);margin-top:40px;padding-top:20px;border-top:1px solid rgba(255,255,255,0.06);text-align:center}
  </style>
</head>
<body>
  <div class="container">
    <div class="badge">EduTrack</div>
    <h1>EduTrack — CSA Spring Boot Project</h1>
    <p>A Spring-based database system to manage mini-courses, grades, and secure spreadsheet imports with full audit trails.</p>

    <h2>Overview</h2>
    <p>This backend project demonstrates advanced database design with Spring Boot, focusing on grade management, versioning, and data import validation. It builds on your SQLite experience from CSP by introducing enterprise patterns like audit trails, role-based access control, and transaction management.</p>

    <h2>Core Features</h2>
    <ul class="list">
      <li><strong>Course & Checkpoint Management</strong> — Define courses with multiple checkpoints (mini-assessments) that students must pass</li>
      <li><strong>User Roles</strong> — Student and Instructor roles with different permissions enforced through Spring Security</li>
      <li><strong>Grade History & Audit Trail</strong> — Every grade change is versioned with timestamp and user tracking for complete auditability</li>
      <li><strong>Spreadsheet Import System</strong> — Upload CSV/XLSX files to bulk-import grades with validation and error logging</li>
      <li><strong>Security</strong> — Spring Security handles authentication and role-based authorization</li>
    </ul>

    <h2>Database Schema</h2>
    
    <div class="entity-box">
      <h3>Course</h3>
      <p>Represents a class or subject area</p>
      <ul class="list">
        <li>id (Primary Key)</li>
        <li>title</li>
        <li>description</li>
        <li>created_at</li>
      </ul>
    </div>

    <div class="entity-box">
      <h3>Checkpoint</h3>
      <p>Mini-assessments within a course that students must complete</p>
      <ul class="list">
        <li>id (Primary Key)</li>
        <li>course_id (Foreign Key → Course)</li>
        <li>name</li>
        <li>pass_score (minimum score to pass)</li>
        <li>max_score</li>
        <li>description</li>
      </ul>
    </div>

    <div class="entity-box">
      <h3>Student</h3>
      <p>Student user profile and enrollment information</p>
      <ul class="list">
        <li>id (Primary Key)</li>
        <li>name</li>
        <li>email (unique)</li>
        <li>student_id</li>
        <li>enrolled_courses (Many-to-Many with Course)</li>
      </ul>
    </div>

    <div class="entity-box">
      <h3>Grade</h3>
      <p>Current grade for a student on a specific checkpoint</p>
      <ul class="list">
        <li>id (Primary Key)</li>
        <li>student_id (Foreign Key → Student)</li>
        <li>checkpoint_id (Foreign Key → Checkpoint)</li>
        <li>score</li>
        <li>passed (boolean, auto-calculated)</li>
        <li>last_updated</li>
      </ul>
    </div>

    <div class="entity-box">
      <h3>GradeHistory</h3>
      <p>Audit trail of all grade changes</p>
      <ul class="list">
        <li>id (Primary Key)</li>
        <li>grade_id (Foreign Key → Grade)</li>
        <li>old_score</li>
        <li>new_score</li>
        <li>changed_by (instructor id)</li>
        <li>changed_at (timestamp)</li>
        <li>reason (optional comment)</li>
      </ul>
    </div>

    <h2>REST API Endpoints</h2>
    <ul class="list">
      <li><strong>POST /api/courses</strong> — Create a new course</li>
      <li><strong>GET /api/courses</strong> — List all courses</li>
      <li><strong>POST /api/checkpoints</strong> — Add checkpoint to a course</li>
      <li><strong>POST /api/grades</strong> — Record or update a grade (creates history entry)</li>
      <li><strong>GET /api/students/{id}/grades</strong> — Get all grades for a student</li>
      <li><strong>GET /api/grades/{id}/history</strong> — View complete audit trail for a grade</li>
      <li><strong>POST /api/import/spreadsheet</strong> — Upload CSV/XLSX to bulk import grades</li>
      <li><strong>GET /api/analytics/checkpoint/{id}/statistics</strong> — Pass rates, averages, distributions</li>
    </ul>

    <h2>Key Technical Implementations</h2>
    
    <h3>Grade Versioning System</h3>
    <p>When a grade is updated, automatically create a GradeHistory entry capturing the old value, new value, who made the change, and when. This creates a complete audit trail.</p>

    <h3>Spreadsheet Import Pipeline</h3>
    <ol class="list">
      <li>Parse uploaded file using Apache POI (Excel) or OpenCSV</li>
      <li>Validate schema: check headers match expected format</li>
      <li>Validate data: ensure student IDs exist, scores are in valid range</li>
      <li>Log validation errors without stopping entire import</li>
      <li>Use Spring @Transactional to ensure all-or-nothing import</li>
      <li>Create Grade and GradeHistory entries for each valid row</li>
    </ol>

    <h3>Analytics Queries</h3>
    <p>Use Spring Data JPA with custom @Query annotations to compute statistics:</p>
    <ul class="list">
      <li>Average score per checkpoint</li>
      <li>Pass/fail rate for each checkpoint</li>
      <li>Students who haven't passed specific checkpoints</li>
      <li>Grade distribution histograms</li>
      <li>Student performance trends over time</li>
    </ul>

    <h2>Development Milestones</h2>
    <ol class="list">
      <li><strong>Week 1:</strong> Design ER diagram and define API contract (OpenAPI/Swagger)</li>
      <li><strong>Week 2:</strong> Set up Spring Boot project with PostgreSQL/MySQL and Flyway migrations</li>
      <li><strong>Week 3:</strong> Implement CRUD operations for courses, checkpoints, and students</li>
      <li><strong>Week 4:</strong> Build grade versioning system with automatic history tracking</li>
      <li><strong>Week 5:</strong> Implement spreadsheet import with validation and error handling</li>
      <li><strong>Week 6:</strong> Add analytics endpoints and Spring Security integration</li>
    </ol>

    <h2>Technologies</h2>
    <ul class="list">
      <li><strong>Spring Boot</strong> — Main framework</li>
      <li><strong>Spring Data JPA</strong> — Database abstraction</li>
      <li><strong>PostgreSQL or MySQL</strong> — Relational database</li>
      <li><strong>Flyway</strong> — Database migrations</li>
      <li><strong>Apache POI</strong> — Excel file parsing</li>
      <li><strong>OpenCSV</strong> — CSV file parsing</li>
      <li><strong>Spring Security</strong> — Authentication & authorization</li>
      <li><strong>JUnit & Mockito</strong> — Testing</li>
    </ul>

    <footer>Ready to start? Need help with ER diagrams, SQL migration scripts, or Spring Boot starter code?</footer>
  </div>
</body>
</html>