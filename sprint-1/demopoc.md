# POC for OT-MICROSERVICES/frontend (Without Docker)

## 1. Purpose
This project is the main frontend UI for the OT-Microservices stack, built using ReactJS. It provides a user interface for managing employees, attendance, and salaries by communicating with backend REST APIs.

## 2. Prerequisites
- Node.js (v16.15.1 recommended)
- npm (comes with Node.js)
- Access/configuration for the following backend REST APIs:
  - [Employee API](https://github.com/OT-MICROSERVICES/employee-api)
  - [Attendance API](https://github.com/OT-MICROSERVICES/attendance-api)
  - [Salary API](https://github.com/OT-MICROSERVICES/salary-api)

## 3. Dependencies
- ReactJS
- tabler-react
- react-router-dom
- react-c3js
- @elastic/apm-rum-react (optional, for performance monitoring)
- @progress/kendo-react-pdf (for PDF export)
- All other dependencies are managed in `package.json`

## 4. System Requirements
- OS: Windows, MacOS, or Linux
- RAM: 2GB+ recommended
- CPU: Any modern processor
- Disk: 200MB+ free space
- Network: Access to backend REST APIs

## 5. How to Build & Run (Without Docker)

1. **Install dependencies:**
    ```bash
    npm install
    ```

2. **Build the application:**
    ```bash
    npm run build
    ```

3. **Run locally (development mode):**
    ```bash
    npm start
    ```
   - The app will be available at [http://localhost:3000](http://localhost:3000)
   - Ensure the backend APIs are running and accessible.

## 6. High-Level Architecture Diagram

![Frontend Architecture](./static/frontend.png)

- The frontend communicates directly with the Employee, Attendance, and Salary APIs.

## 7. References

- [OT-MICROSERVICES Organization](https://github.com/OT-MICROSERVICES)
- Contact: Opstree Opensource (opensource@opstree.com)

---

You now have the essentials to start a POC for this ReactJS frontend, without Docker. For further customization or integration, refer to the code and documentation within the repository.
