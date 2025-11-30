Employee Management Portal – Frontend (Angular)

This is the Frontend Application for the Employee Management Portal, built using Angular.
The frontend interacts with the .NET Core API to manage employees, departments, and project summaries.
 Tech Stack

Angular 13+

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


Build output will be available in:

/dist/

