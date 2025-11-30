Employee Management Portal – Frontend (Angular)

This is the Frontend Application for the Employee Management Portal, built using Angular.
The frontend interacts with the .NET Core API to manage employees, departments, and project summaries.
 Tech Stack

Angular 20

TypeScript

RxJS / Observables

HTML / SCSS / Bootstrap / Material (as per your project)

REST API Integration

Project Structure
src/
 ├── app/
 │   ├── pages/
 │   │   ├── employee-list/
 │   │   ├── employee-add/
 │   │   ├── employee-summary/
 │   ├── services/
 │   │   ├── employee.service.ts
 │   │   ├── department.service.ts
 │   ├── app.routes.ts
 │   ├── app.ts
 ├── assets/
 ├── environments/

 Prerequisites

Before running this Angular project, make sure you have:

Tool	Version
Node.js	16+
Angular CLI	13+
npm	8+
Backend API	Running (.NET Core API)
 Installation & Setup
1. Clone the repository
git clone https://github.com/your-repo/employee-management-angular.git
cd employee-management-angular

2. Install dependencies
npm install

3. Setup environment file

Go to:

src/environments/environment.ts


Add your API URL:

export const environment = {
  production: false,
  apiUrl: "https://localhost:7000/api"
};

 Run the Application

Start Angular project:

ng serve --open


It will run on:

http://localhost:4200/

 Available Pages
1. Employee List Page

Fetch employees from /api/employees

Department filter (dropdown)

Searching, sorting, pagination

Inline actions (Edit/Delete)

 2. Add Employee Page

Form fields:

First Name

Last Name

Email

Salary

Department

Date of Joining

Active Status

Validations:

Required fields

Email format check

Salary > 0

Date cannot be in the future

Calls API → POST /api/employees

3. Employee Project Summary Page

Fetch summary from /api/employees/projects

Shows count of assigned projects

Optional drill-down

API Integration

All API calls are handled through Angular Services:

Example: EmployeeService
getEmployees() {
  return this.http.get(`${this.baseUrl}/employees`);
}

 UI/UX

Clean and modern layout

Responsive design

Optional Material UI / Bootstrap integration

Build for Production
ng build --configuration production


------------------------------------------Backend --------------------------------------------------------------------
Employee Management Portal – Backend (.NET Core API)

This is the backend API for my Employee Management Portal project.
The API is built using .NET Core, Entity Framework (Database First), and MS SQL Server.
It provides all the employee, department, and project-related data that the frontend (Angular) consumes.

What this API does

Fetch all employees with department and project details

Add new employees using a stored procedure

Filter employees by department

Get project count assigned to each employee

Basic employee filters like salary range, joining date range, and active/inactive status

Fetch department list

Works fully on database-first structure with Views, Stored Procedures & LINQ queries

 Database Overview

Database Name: EmployeeDB

Tables

Employees

Departments

Projects

EmployeeProjects

View

View that combines Employee + Department + Project info

Stored Procedures

GetEmployeesByDepartment

AddNewEmployee

GetEmployeeProjectSummary

 How to Set Up the API
1. Clone the repository
git clone https://github.com/your-repo/employee-management-api.git
cd employee-management-api

2. Update your connection string

Inside appsettings.json:

"ConnectionStrings": {
  "MyDbConnection": "Server=DESKTOP-DPQTTQ0\SQL2019DEV;Database=EmployeeDB;Trusted_Connection=True;TrustServerCertificate=True;"
}

3. Restore & Build
dotnet restore
dotnet build

4. Run the API
dotnet run


The API will start on:

 https://localhost:7000/api
 Available Endpoints
Employees
Method	Endpoint	Purpose
GET	/api/employees	Get all employees (using view)
GET	/api/employees/department/{id}	From stored procedure
POST	/api/employees	Add employee (stored procedure)
GET	/api/employees/filter	Salary, date, status filters (LINQ)
GET	/api/employees/projects	Project count summary
Departments
Method	Endpoint
GET	/api/departments
Model Validations

FirstName & LastName → required

Email → required + must be unique

Salary → must be greater than 0

Department → must exist

DateOfJoining → cannot be in the future

IsActive → required
 EF Database First

I generated all models using:

Scaffold-DbContext "Server=DESKTOP-DPQTTQ0\SQL2019DEV;Database=EmployeeDB;Trusted_Connection=True;" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -f

 Build for Production
dotnet publish -c Release


Files will be available inside:

/bin/Release/net6.0/publish

‍Why I built it

I created this backend as part of a full-stack assessment to demonstrate:

My knowledge of .NET Core

Database-first development

Writing clean and structured APIs

Using stored procedures and views with EF

Applying proper validations and LINQ filters













Build output will be available in:

/dist/


