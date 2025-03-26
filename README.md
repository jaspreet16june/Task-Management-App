# Task-Management-System

### Overview

The Task Management API is a Django REST Framework (DRF) project that allows users to create, assign, and update tasks. It also provides user management functionalities.

### Features

1. CRUD operations for tasks and users
2. Assign multiple users to a task
3. Prevent updates on completed tasks
4. Filter tasks by assigned users

### Technologies Used
1. Django
2. Django REST Framework (DRF)
3. Python 3.10.12


## Installation

### Prerequisites:
1. Ensure you have the following installed:
2. Python 3.10.12
3. Django
4. Django REST Framework

### Setup:

1. Clone the repository:
    ```bash
    git clone https://github.com/jaspreet16june/Task-Management-System.git
    cd task-management
    ```
2. Create and activate a virtual environment:
    ```bash
    virtualenv task_env
    source task_env/bin/activate  # On Windows use: task_env\Scripts\activate
    ```
3. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
4. Apply database migrations:
   ```bash
   python manage.py migrate
   ```
5. Create a superuser (optional):
   ```bash
   python manage.py createsuperuser
   ```
6. Start the development server:
   ```bash
   python manage.py runserver
   ```

## API Endpoints

### User Endpoints
| Method | Endpoint       | Description        |
|--------|--------------|--------------------|
| GET    | `/users/`    | List all users     |
| POST   | `/users/`    | Create a user      |

### Task Endpoints
| Method | Endpoint       | Description        |
|--------|--------------|--------------------|
| GET    | `/tasks/`    | List all tasks     |
| POST   | `/tasks/`    | Create a new task  |
| GET    | `/tasks/{id}/` | Retrieve task details |
| POST    | `/tasks/{id}/` | Update a task Or User Assignment     |


### Filtering Tasks by User
To retrieve tasks assigned to a specific user, use the query parameter:
```
GET /tasks/?user_id=<user_id>
```

## Models

### User Model
- `name`: User's full name
- `email`: Unique email address
- `mobile_no`: Contact number
- `created_at`: Timestamp of account creation
- `modified_at`: Timestamp of last modification

### Task Model
- `name`: Task title
- `description`: Task details
- `task_type`: Category/type of task
- `status`: Current task status (e.g., `pending`, `completed`)
- `completed_at`: Timestamp when the task was completed
- `assigned_users`: Users assigned to the task

## Serializers

### UserSerializer
Handles the serialization of `User` model objects.

### TaskSerializer
Handles task creation, updating, and assignment of users. Prevents updates if the task status is `completed`.

## Error Handling
- If an attempt is made to update a completed task, an error is raised: `{ "error": "Cannot update a completed task." }`
- If a requested task or user does not exist, a `404 Not Found` response is returned.

## Conclusion
This Task Management API is a robust solution for handling tasks and user assignments in a team environment. It ensures proper validation, structured responses, and efficient querying.



