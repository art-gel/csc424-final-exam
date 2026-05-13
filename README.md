DevOps Setup

Local Development:
  - To run the full stack locally, use the following command: docker compose up --build -d
  - This line builds the project (frontend + backend) by starting every container and runs
    them in the background (-d=detached mode). Essentially, only one command is needed to launch
    the full project in one go, which makes things easier!

Accessing the Application:
  - Once the containers are up and running, the application can be accssible with the following URLs:
    -   frontend = http://localhost (Port 80).
    -   backend API Health Check = http://localhost/api/ping.

Main Services Overview:
  - The project consists of 3 important services:
    -   The frontend is the UI homepage in which users can interact within the browser.
    -   The backend is the server-side of the application that handles requests and
        returns reponses such as /api/ping. The health check is to verify that the API is functioning
        without any errors.
    -   Nginx functions as a reverse proxy and entry point, meaning it routes external traffic on Port 80.
        For example, /api requests would be routed to the backend and / goes to the frontend of the               application.
        
CI/CD Pipeline Process:
  - The pipeline automatticly deploys to GitHub Actions whenever the code is pushed to the main branch.
  - Then, GitHub Actions builds the Docker images for the frontend and backend.
  - The pipeline securely connects to the QA Server via SSH by using the hidden private key stored on         GitHub Secrets.
  - the lastes images are pulled and using docker compose command restarts the containers.
  - This process ensures the lastest version is up to date without manual setup. 
