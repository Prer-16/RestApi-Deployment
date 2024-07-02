
# Implementation of REST API to get Linux System details

This project involves the implementation of a REST API on a Linux system for retrieving server/ system details. The API is designed to interact with the server using standard HTTP methods and provides well-defined endpoints for accessing various system information. By deploying this project to a server (Linux Server), users can easily fetch details such as CPU usage, memory usage, harddisks details, user details and other relevant system metrics through HTTP requests.



## Installation

Verify Linux OS on server
```bash
 uname -a
 ```
Expected response
```bash
linux
```
Check for JDK
```bash
java -version
```
If not installed, install JDK
```bash
sudo apt-get update
sudo apt-get install -y openjdk-17-jdk
```
Check for MySQL
```bash
mysql --version
```
If not installed, install MySQL
```bash
sudo apt-get update
sudo apt-get install -y mysql-server
sudo systemctl start mysql
sudo systemctl enable mysql
```

## Tech Stack

**SERVER:** Embedded tomcat 

**JAR FILE:**

Generate JAR (JAVA ARCHIVE) file in the IDE  that Contains annotations and binds dependencies.

#### SCRIPT FILE

### 1. Define application.properties File 

This configuration file contains the following:

### Spring datasource configuration
spring.datasource.url=jdbc:mysql://localhost:3306/your_database_name
spring.datasource.username=your_username
spring.datasource.password=your_password


### Fix the port

server.port = your_port_number
### Specify the driver class for MySQL
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

### Hibernate settings
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect


### Database Configuration: Details on connecting to the MySQL database.
DB_NAME="your_database_name" 

DB_USER="your_username"

DB_PASSWORD="your_password"

## 2. Start the Spring Boot application with embedded application.properties
java -jar -Dspring.config.location=file:./application.properties your_application.jar



## Deployment

**gFTP client** is a free and open-source FTP client for Linux.

Download it through commands or GUI 

Fill in your FTP credentials and FTP server details and hit the connect button and then we  can push the files.

**Transfer of MySQL DB:**

import database to sql.dump file

**Push Files:** Place jar file, script.sh in the same folder,import sql.dump to the server's database with same DB_NAME.

**SSH Connection Setup:**
1.	SSH Installation (if not installed)
    Install SSH client:
```bash 
sudo apt-get update
sudo apt-get install -y openssh-client
```
2.	Establish SSH Connection:
```bash
Syntax: username@ip_address
Provide credentials (password or SSH key):
ssh username@ip_address
```
3. Server Setup and Execution:

    1. Navigate to Deployment Folder:
```bash
cd /path/to/deployment_folder
```
2.	Set Permissions:
```bash 
Ensure executable permissions:
chmod 777 script.sh
chmod +x script.sh
```

3.	Run Script
```bash
./script.sh
```
 Run Script with nohup (Execute script with nohup to keep it running after terminal session ends)
 ```bash
nohup ./script.sh &
```







## Running Tests

**Testing Using a Web Browser:**

http://<server_ip>:<port>/api_endpoint
```bash 
(example) http://192.168.2.30:8089/system/users
```
**Testing Using Postman:**

http://<server_ip>:<port>/api_endpoint

Add Headers or Parameters (if needed)

**Send Request:**

•	Click on the "Send" button to send the request to your server.

 **View Response:**

•	Postman will display the response from your REST API. Verify that it returns the expected data and status code.



