# 🚀 How to Deploy **DSOC3-WebApp** on Ubuntu with OpenJDK 25, Maven 3.8.7, and Tomcat 10

This tutorial walks you through deploying the [**DSOC3-WebApp**](https://github.com/dsoc3/DSOC3-WebApp.git) — a Java Servlet-based Application — on Ubuntu using **OpenJDK 25**, **Apache Maven 3.8.7**, and **Tomcat 10**.

---

## 🧰 Prerequisites

Before you begin, ensure you have:

* 🐧 **Ubuntu 24.04** or later
* 🌐 Internet access
* 🔑 **Sudo privileges**

---

## ⚙️ Step-by-Step Deployment Guide

### 🧩 1. Update Your System

Keep your packages up to date:

```bash
sudo apt update -y && sudo apt upgrade -y
```

---

### ☕ 2. Search for Available Java Packages

List all available OpenJDK versions:

```bash
apt-cache search openjdk
```

---

### 🧑‍💻 3. Install OpenJDK 25

Install the latest Java Development Kit:

```bash
sudo apt install openjdk-25-jdk -y
```

Verify installation:

```bash
java -version
```

---

### 🔧 4. Install Apache Maven 3.8.7

Install Maven:

```bash
sudo apt install maven -y
```

Check version:

```bash
mvn -v
```

---

### 🧬 5. Clone the DSOC3-WebApp Repository

```bash
git clone https://github.com/dsoc3/DSOC3-WebApp.git
cd DSOC3-WebApp
```

---

### 🏗️ 6. Build the Project

Clean and build the project:

```bash
mvn clean install
```

This generates the WAR file:
📁 `target/dsoc3-webapp.war`

---

### 🔍 7. Search for Tomcat Packages

```bash
apt-cache search tomcat
```

---

### 🐱‍👤 8. Install Tomcat 10

Install Tomcat:

```bash
sudo apt install tomcat10 -y
```

Check Tomcat status:

```bash
sudo systemctl status tomcat10.service
```

---

### 📦 9. Deploy the WAR File

Copy your built WAR file to the Tomcat webapps directory:

```bash
sudo cp target/dsoc3-webapp.war /var/lib/tomcat10/webapps/
```

Verify it’s in place:

```bash
ls -lrt /var/lib/tomcat10/webapps
```

---

### 🔁 10. Restart Tomcat

Restart the Tomcat service:

```bash
sudo systemctl restart tomcat10
```

Confirm it’s running:

```bash
sudo systemctl status tomcat10.service
```

---

### 🌍 11. Access the Web Application

Open your browser and visit:

```
http://localhost:8080/dsoc3-webapp
```

Or use your machine’s IP address if accessing remotely.

---

## ✅ Conclusion

🎉 Congratulations! You’ve successfully deployed **DSOC3-WebApp** on Ubuntu using:

* ☕ **OpenJDK 25**
* 🔧 **Maven 3.8.7**
* 🐱‍👤 **Tomcat 10**

This setup is perfect for Java servlet-based applications and can be easily extended with:

* 🌐 **Nginx reverse proxy**
* 🔒 **HTTPS configuration**
* 🐳 **Docker containerization**

---
