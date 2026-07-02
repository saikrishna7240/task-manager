# API Documentation

## Base URL

```
/api
```

---

# Authentication APIs

## Register User

**Endpoint**

```
POST /api/auth/register
```

### Request Body

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "Password123"
}
```

### Success Response

```json
{
  "message": "User registered successfully"
}
```

---

## Login User

**Endpoint**

```
POST /api/auth/login
```

### Request Body

```json
{
  "email": "john@example.com",
  "password": "Password123"
}
```

### Success Response

```json
{
  "token": "JWT_TOKEN"
}
```

---

## Get User Profile

**Endpoint**

```
GET /api/users/profile
```

### Headers

```
Authorization: Bearer <JWT_TOKEN>
```

---

## Update User Profile

**Endpoint**

```
PUT /api/users/profile
```

### Headers

```
Authorization: Bearer <JWT_TOKEN>
```

---

# Task APIs

## Get All Tasks

**Endpoint**

```
GET /api/tasks
```

### Query Parameters

| Parameter | Description                      |
| --------- | -------------------------------- |
| search    | Search tasks by title            |
| category  | Filter by category               |
| priority  | Filter by priority               |
| status    | Filter by status                 |
| sort      | Sort by due date or created date |

### Example

```
GET /api/tasks?status=Pending&priority=High
```

---

## Get Task by ID

**Endpoint**

```
GET /api/tasks/:id
```

---

## Create Task

**Endpoint**

```
POST /api/tasks
```

### Request Body

```json
{
  "title": "Complete Backend",
  "description": "Build authentication APIs",
  "category": "Study",
  "priority": "High",
  "dueDate": "2026-07-10"
}
```

### Success Response

```json
{
  "message": "Task created successfully"
}
```

---

## Update Task

**Endpoint**

```
PUT /api/tasks/:id
```

### Request Body

```json
{
  "title": "Updated Task",
  "description": "Updated description",
  "category": "Work",
  "priority": "Medium",
  "status": "Pending",
  "dueDate": "2026-07-12"
}
```

---

## Delete Task

**Endpoint**

```
DELETE /api/tasks/:id
```

### Success Response

```json
{
  "message": "Task deleted successfully"
}
```

---

## Update Task Status

**Endpoint**

```
PATCH /api/tasks/:id/status
```

### Request Body

```json
{
  "status": "Completed"
}
```

---

# Dashboard API

## Get Dashboard Statistics

**Endpoint**

```
GET /api/dashboard
```

### Response

```json
{
  "totalTasks": 25,
  "completedTasks": 18,
  "pendingTasks": 7,
  "overdueTasks": 2,
  "completionPercentage": 72
}
```

---

# Authentication

All APIs except Register and Login require a JWT token.

### Header

```
Authorization: Bearer <JWT_TOKEN>
```

---

# HTTP Status Codes

| Code | Description           |
| ---- | --------------------- |
| 200  | OK                    |
| 201  | Created               |
| 400  | Bad Request           |
| 401  | Unauthorized          |
| 403  | Forbidden             |
| 404  | Not Found             |
| 500  | Internal Server Error |

---

# API Version

```
v1
```

---

# Future APIs

* Forgot Password
* Reset Password
* Email Verification
* Upload Attachments
* Notifications
* Task Comments
* Task Labels
* Team Collaboration
* Activity Logs
