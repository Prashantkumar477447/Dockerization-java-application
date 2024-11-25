# Docker project
# Java Application Dockerization Project

This project demonstrates how to dockerize a Java application by creating a Dockerfile, building a Docker image, and running it as a container in Windows PowerShell. This repository provides a complete guide and necessary files to containerize a simple Java application.

---

## **Features**
- A step-by-step guide to containerizing a Java application.
- Usage of Docker to ensure consistent runtime environments.
- Build, run, and test the containerized application on any system with Docker installed.

---

## **Prerequisites**
1. **Docker Installed on Windows**:  
   Install Docker Desktop for Windows and ensure it is running. [Download Docker Desktop](https://www.docker.com/products/docker-desktop/)

2. **Java Development Kit (JDK)**:  
   Ensure JDK is installed to compile the Java application.

3. **Windows PowerShell**:  
   Open a terminal to execute Docker commands.
   
---

## **Project Structure**
```plaintext
├── Dockerfile             # Instructions for building the Docker image
├── src/                   # Java source code directory
│   └── Main.java          # Simple Java application entry point
├── README.md              # Project documentation
└── target/                # Compiled Java application (created after build)
    └── app.jar            # Packaged JAR file of the application
```

---

## **Steps to Run the Project**

### **1. Clone the Repository**
Clone this GitHub repository to your local machine:
```bash
git clone https://github.com/your-username/java-docker-project.git
cd java-docker-project
```
![Screenshot 2024-11-25 134455](https://github.com/user-attachments/assets/bc11ea21-475a-46b6-9919-b41be2f4bf42)

---

### **2. Compile the Java Application**
Navigate to the `src/` folder and compile the `Main.java` file:
```powershell
javac -d ../target src/Main.java
```

Then package the compiled code into a `.jar` file:
```powershell
jar -cvf target/app.jar -C target .
```

---

### **3. Create the Dockerfile**
Ensure the `Dockerfile` in the root directory contains the following:
```dockerfile
# Use OpenJDK 17 base image
FROM openjdk:17-jdk-alpine

# Set the working directory in the container
WORKDIR /app

# Copy the JAR file into the container
COPY target/app.jar app.jar

# Run the application
CMD ["java", "-jar", "app.jar"]
```
![Screenshot 2024-11-25 125352](https://github.com/user-attachments/assets/e72a3671-9d80-4fc0-bf0b-1e96e38ec09a)

---

### **4. Build the Docker Image**
Use the following command in PowerShell to build the Docker image:
```powershell
docker build -t java-app .
```
![Screenshot 2024-11-25 134544](https://github.com/user-attachments/assets/cb837f37-0746-4a43-b31a-f130fdd335b3)

---

### **5. Run the Docker Container**
Start a container using the built image:
```powershell
docker run -it java-app
```
![Screenshot 2024-11-25 134609](https://github.com/user-attachments/assets/4415205b-2649-4a29-a54c-75a1014b72dd)

---

### **6. Verify the Application**
After running the container, you should see the output of your Java application in the terminal.
![Screenshot 2024-11-25 134641](https://github.com/user-attachments/assets/bbbba57c-676f-491f-bc6a-c475dc10100a)

---

## **Common Commands**

### **List Docker Images**
```powershell
docker images
```

### **Stop Running Containers**
```powershell
docker ps           # List running containers
docker stop <CONTAINER_ID>
```

### **Remove Docker Containers**
```powershell
docker rm <CONTAINER_ID>
```

---

## **Future Enhancements**
- Add support for environment variables.
- Automate builds with GitHub Actions.
- Include a multi-stage build for more efficient image sizes.

---

## **License**
This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

Feel free to contribute to this project by opening issues or submitting pull requests! 😊
