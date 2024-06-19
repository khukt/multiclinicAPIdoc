# multiclinicAPIdoc
Multi Clinic API documentation
Yes, based on the structure of the provided project, the `PatientController` handles operations related to patient information, and it includes these five primary endpoints. Here is a refined and detailed documentation for these API endpoints.

## MultiClinic API Documentation

### Base URL
`http://localhost:5000`

### Endpoints Overview

1. **Patients**
   - `GET /api/patients` - Retrieve all patients.
   - `GET /api/patients/{id}` - Retrieve a specific patient by ID.
   - `POST /api/patients` - Create a new patient.
   - `PUT /api/patients/{id}` - Update an existing patient by ID.
   - `DELETE /api/patients/{id}` - Delete a patient by ID.

---

### Detailed Endpoints

#### 1. Get All Patients

**Endpoint:** `GET /api/patients`

**Description:** Retrieves a list of all patients.

**Request Example:**
```sh
curl -X GET "http://localhost:5000/api/patients"
```

**Response:**
- **200 OK**
- **Body:**
  ```json
  [
    {
      "id": 1,
      "name": "John Doe",
      "status": "Active"
    },
    {
      "id": 2,
      "name": "Jane Smith",
      "status": "Inactive"
    }
  ]
  ```

**Errors:**
- **500 Internal Server Error**: If there is an issue retrieving the patients.

#### 2. Get Patient by ID

**Endpoint:** `GET /api/patients/{id}`

**Description:** Retrieves details of a specific patient by ID.

**Parameters:**
- `id` (path): The ID of the patient to retrieve.

**Request Example:**
```sh
curl -X GET "http://localhost:5000/api/patients/1"
```

**Response:**
- **200 OK**
- **404 Not Found**
- **Body:**
  ```json
  {
    "id": 1,
    "name": "John Doe",
    "status": "Active"
  }
  ```

**Errors:**
- **404 Not Found**: If the patient with the specified ID does not exist.
- **500 Internal Server Error**: If there is an issue retrieving the patient.

#### 3. Create a New Patient

**Endpoint:** `POST /api/patients`

**Description:** Creates a new patient record.

**Request Body:**
```json
{
  "name": "John Doe",
  "status": "Active"
}
```

**Request Example:**
```sh
curl -X POST "http://localhost:5000/api/patients" -H "Content-Type: application/json" -d '{"name": "John Doe", "status": "Active"}'
```

**Response:**
- **201 Created**
- **400 Bad Request**
- **Body:**
  ```json
  {
    "id": 3,
    "name": "John Doe",
    "status": "Active"
  }
  ```

**Errors:**
- **400 Bad Request**: If the request body is invalid.
- **500 Internal Server Error**: If there is an issue creating the patient.

#### 4. Update an Existing Patient

**Endpoint:** `PUT /api/patients/{id}`

**Description:** Updates an existing patient record by ID.

**Parameters:**
- `id` (path): The ID of the patient to update.

**Request Body:**
```json
{
  "name": "John Doe",
  "status": "Inactive"
}
```

**Request Example:**
```sh
curl -X PUT "http://localhost:5000/api/patients/1" -H "Content-Type: application/json" -d '{"name": "John Doe", "status": "Inactive"}'
```

**Response:**
- **200 OK**
- **404 Not Found**
- **400 Bad Request**
- **Body:**
  ```json
  {
    "id": 1,
    "name": "John Doe",
    "status": "Inactive"
  }
  ```

**Errors:**
- **404 Not Found**: If the patient with the specified ID does not exist.
- **400 Bad Request**: If the request body is invalid.
- **500 Internal Server Error**: If there is an issue updating the patient.

#### 5. Delete a Patient

**Endpoint:** `DELETE /api/patients/{id}`

**Description:** Deletes a patient record by ID.

**Parameters:**
- `id` (path): The ID of the patient to delete.

**Request Example:**
```sh
curl -X DELETE "http://localhost:5000/api/patients/1"
```

**Response:**
- **200 OK**
- **404 Not Found**
- **Body:**
  ```json
  {
    "message": "Patient deleted successfully."
  }
  ```

**Errors:**
- **404 Not Found**: If the patient with the specified ID does not exist.
- **500 Internal Server Error**: If there is an issue deleting the patient.

---

### Using the API with Postman

1. **Open Postman** and create a new request.

2. **Get All Patients:**
   - **Method:** GET
   - **URL:** `http://localhost:5000/api/patients`
   - **Send** the request and check the response.

3. **Get Patient by ID:**
   - **Method:** GET
   - **URL:** `http://localhost:5000/api/patients/1`
   - **Send** the request and check the response.

4. **Create a New Patient:**
   - **Method:** POST
   - **URL:** `http://localhost:5000/api/patients`
   - **Body:** 
     ```json
     {
       "name": "John Doe",
       "status": "Active"
     }
     ```
   - **Send** the request and check the response.

5. **Update an Existing Patient:**
   - **Method:** PUT
   - **URL:** `http://localhost:5000/api/patients/1`
   - **Body:** 
     ```json
     {
       "name": "John Doe",
       "status": "Inactive"
     }
     ```
   - **Send** the request and check the response.

6. **Delete a Patient:**
   - **Method:** DELETE
   - **URL:** `http://localhost:5000/api/patients/1`
   - **Send** the request and check the response.

---

### Configuration

#### appsettings.json

This file contains the configuration settings for the API. Key settings might include:

- **Connection Strings**: Defines how the API connects to the database.
- **Logging**: Configures logging levels and providers.

**Example appsettings.json**:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=MultiClinic;Trusted_Connection=True;"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

### Running the Project

1. **Build the Solution:**
   - Open the solution file `MultiClinic.sln` in Visual Studio.
   - Build the solution to restore dependencies and compile the projects.

2. **Run Migrations:**
   - Open a command prompt or terminal.
   - Navigate to the `MultiClinic.EntityFramework` project directory.
   - Run the following command to apply migrations:
     ```bash
     dotnet ef database update
     ```

3. **Start the API:**
   - Set the `MultiClinic.API` project as the startup project in Visual Studio.
   - Run the project to start the web API.
   - Alternatively, use the following command to run the API from the command line:
     ```bash
     dotnet run --project MultiClinic.API
     ```

4. **Docker:**
   - Ensure Docker is installed and running.
   - Navigate to the `MultiClinic.API` project directory.
   - Build the Docker image using the following command:
     ```bash
     docker build -t multiclinc-api .
     ```
   - Run the Docker container using the following command:
     ```bash
     docker run -p 8080:80 multiclinc-api
     ```

---
