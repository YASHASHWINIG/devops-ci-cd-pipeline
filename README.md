CI/CD Pipeline Project
-Project Overview
    This project demonstrates real-time CI/CD pipeline implementation using industry tools.
    This project demonstrates a complete CI/CD pipeline using Jenkins, Maven, SonarQube, Nexus, and Tomcat.
    The pipeline automates build, test, quality check, artifact storage, and deployment of a Java application.
    
     -Architecture
GitHub → Jenkins → SonarQube → Nexus → Tomcat → Browser

    CI/CD Pipeline Flow
01.Code is stored in GitHub
02.Jenkins pulls the code from GitHub
03.Maven builds and tests the project
04.SonarQube analyzes code quality
05.Nexus stores the build artifact (.war file)
06.Jenkins deploys the application to Tomcat server
07.Application runs in browser

   Tools & Technologies
01.Jenkins (CI/CD)
02.Maven (Build tool)
03.SonarQube (Code Quality)
04.Nexus (Artifact Repository)
05.Tomcat (Deployment Server)
06.AWS EC2 (Hosting)
07.GitHub (Version Control)

   Key Features
01. Automated CI/CD pipeline
02. Code quality analysis using SonarQube
03. Artifact storage in Nexus repository
04. Deployment to Tomcat server
05. End-to-end DevOps workflow
