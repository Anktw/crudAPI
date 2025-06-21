# CRUDAPI

CRUDAPI is a collaborative to-do list API built with Java Spring Boot and MongoDB. It implements APIs to create, manage, and share their tasks with team members, enhancing productivity and collaboration.

## Features

- **User Management**: Create and manage user accounts.
- **Collaborative Tasks**: Share tasks with team members and collaborate in real-time.
- **Task Management**: Create, update, delete, and list tasks.
- **Categorization**: Create Groups where people can come together to work a Project.
- **Priority Levels**: Assign priority levels to tasks.
- **Due Dates**: Set and manage due dates for tasks.

## Getting Started

| Variable        | Value                                                   |
|-----------------|---------------------------------------------------------|
| MONODB_URI      | Your MongoDB URI link with username and password        |
| JWT_SECRECT_KEY | At least 256-bits Secret Key for HMAC-SHA               |
| FRONTEND_URL    | Frontend URL to connect with backend using @CrossOrigin |
| MAIL_USERNAME   | Your mail username                                      |
| MAIL_PASSWORD   | Your generated app-specific password.                   |


## Endpoints

| Method | Endpoint                          | Description                                              |
|--------|-----------------------------------|----------------------------------------------------------|
| POST   | `auth/sign-in`                    | Create a new user and send confirmation code.            |
| POST   | `auth/log-in`                     | Log in via JWT.                                          |
| POST   | `auth/verify-confirmation`        | Verify user confirmation.                                |
| GET    | `health-check`                    | Check if the app is working.                             |
| PUT    | `user/update-username`            | Update the user's username.                              |
| GET    | `admin/all-users`                 | Retrieve all users (admin only).                         |
| POST   | `group/create`                    | Create a new group.                                      |
| DELETE | `group/{groupId}/delete`          | Deletes an existing group.(group admin only)             |
| POST   | `invitation/send`                 | Send an invitation to join the group (group admin only). |
| PUT    | `invitation/{invitationId}/accept` | Accept an invitation to join the group.                  |
| PUT    | `invitation/{invitationId}/reject` | Reject an invitation to join the group.                  |
| POST   | `task/assign`                     | Assign a task to a specific user (group admin only).     |
| PUT    | `task/{taskId}/accept`            | Accept an assigned task.                                 |
| PUT    | `task/{taskId}/reject`            | Reject an assigned task.                                 |
| PUT    | `task/{taskId}/start`             | Start working on an assigned task.                       |
| PUT    | `task/{taskId}/complete`          | Mark a task as completed.                                |

## Group

### Create a Group
- **Endpoint:** `POST /group/create`
- **Request Body:**
  ```json
  {
    "groupName": "name",
    "groupDescription": "description"
  }
  ```

### Delete a Group
- **Endpoint:** `POST /group/{groupId}/delete`

## Group Invitation

### Invite a User to a Group
- **Endpoint:** `POST /group/invite`
- **Request Body:**
  ```json
  {
    "groupId": "groupId",
    "invitedUserName": "userName"
  }
  ```

### Accept an Invitation
- **Endpoint:** `PUT /invitation/{invitationId}/accept`

### Reject an Invitation
- **Endpoint:** `PUT /invitation/{invitationId}/reject`

## Task Management

### Assign a Task
- **Endpoint:** `POST /task/assign`
- **Request Body:**
  ```json
  {
    "groupId": "groupId",
    "title": "title",
    "description": "description",
    "assignedToUserName": "userName",
    "deadline": "yyyy-MM-dd'T'HH:mm:ss"
  }
  ```

### Accept a Task
- **Endpoint:** `PUT /task/{taskId}/accept`

### Reject a Task
- **Endpoint:** `PUT /task/{taskId}/reject`

### Start a Task
- **Endpoint:** `PUT /task/{taskId}/start`

### Complete a Task
- **Endpoint:** `PUT /task/{taskId}/complete`


