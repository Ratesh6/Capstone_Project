
# AWS Java 3-Tier Capstone Project

## Project Overview
This is a **Java-based 3-Tier web application** deployed on AWS, following the classic 3-Tier architecture: **Presentation (Frontend), Application (Backend), and Database (RDS/MySQL)**. The project demonstrates cloud deployment, secure key management, Maven build automation, and best DevOps practices including CI/CD and Dockerization.

## Tech Stack
- **Language:** Java
- **Framework:** Servlet / JSP
- **Build Tool:** Maven
- **Database:** MySQL / AWS RDS
- **Cloud:** AWS EC2, S3
- **Version Control:** Git & GitHub
- **CI/CD:** GitHub Actions (optional)
- **Containerization:** Docker (optional)

## Project Structure
```
aws-java-3tier/
├── .gitignore         # Ignored files (PEM, target)
├── pom.xml            # Maven configuration
├── src/               # Java source code (Servlets, JSPs)
├── screenshots/       # Project screenshots
└── target/            # Maven build output (ignored)
```

## AWS 3-Tier Architecture
```
       [ User / Browser ]
                |
          [ Presentation Tier ]
           (Java Servlet / JSP)
                |
        [ Application Tier ]
           (Business Logic)
                |
           [ Data Tier ]
              (AWS RDS MySQL)
```
**Flow:**
1. User sends HTTP request to EC2-hosted web server (Presentation Tier).
2. Servlets handle the request and call business logic in the Application Tier.
3. Application Tier queries AWS RDS for data.
4. Response is returned to the user.

## How to Run Locally

### Prerequisites
- Java JDK 8+
- Maven 3+
- MySQL running locally (or RDS credentials)

### Steps
1. Clone the repository:
```
git clone https://github.com/Ratesh6/Capstone_Project.git
cd aws-java-3tier
```
2. Build the project:
```
mvn clean install
```
3. Deploy the WAR file to a servlet container (Tomcat):
```
# Example: copy target/aws-java-3tier.war to Tomcat webapps folder
```
4. Access the application:
```
http://localhost:8080/aws-java-3tier
```

## CI/CD Pipeline (GitHub Actions)

Example workflow:
```yaml
name: Java CI

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up JDK
        uses: actions/setup-java@v3
        with:
          java-version: '11'
      - name: Build with Maven
        run: mvn clean install
```

## Dockerization (Optional)
1. Create `Dockerfile`:
```dockerfile
FROM tomcat:9-jdk11
COPY target/aws-java-3tier.war /usr/local/tomcat/webapps/
EXPOSE 8080
```
2. Build Docker image:
```
docker build -t aws-java-3tier-app .
```
3. Run container:
```
docker run -p 8080:8080 aws-java-3tier-app
```

## Security Note
- **Do NOT commit private keys** (`.pem`) or credentials.
- `.gitignore` excludes sensitive files like `capstone-key.pem` and `target/`.

## Screenshots
Include screenshots from `screenshots/` folder showing application pages.

## Author
**Ratesh K** – Bengaluru, India
- Email: rateshk123@gmail.com
- GitHub: [Ratesh6](https://github.com/Ratesh6)

## License
This project is for learning and portfolio purposes.
