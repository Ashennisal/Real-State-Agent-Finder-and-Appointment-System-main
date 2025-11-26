# Real Estate Agent Finder and Appointment System

<div align="center">

![Real Estate Agent Finder Logo](https://via.placeholder.com/150)

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/IT24103866/Real-State-Agent-Finder-and-Appointment-System)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Java](https://img.shields.io/badge/java-17-orange.svg)](https://www.java.com/)
[![Servlet](https://img.shields.io/badge/servlet-4.0-red.svg)](https://jakarta.ee/specifications/servlet/)

**Connect property seekers with real estate professionals through a servlet-based platform with JSON file storage**

[Report Bug](https://github.com/IT24103866/Real-State-Agent-Finder-and-Appointment-System/issues) | [Request Feature](https://github.com/IT24103866/Real-State-Agent-Finder-and-Appointment-System/issues)

</div>

## 📋 Table of Contents

- [System Overview](#-system-overview)
- [Architecture](#-architecture)
- [Technology Stack](#-technology-stack)
- [Core Features](#-core-features)
- [Screenshots](#-screenshots)
- [Getting Started](#-getting-started)
- [Development](#-development)
- [API Reference](#-api-reference)
- [Deployment](#-deployment)
- [Project Structure](#-project-structure)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)

## 🔍 System Overview

The Real Estate Agent Finder and Appointment System is a web application designed to connect property buyers and sellers with qualified real estate agents. Users can search for agents, view their profiles, and schedule appointments through an intuitive interface. The system uses Java servlets for the backend, with data stored in JSON files using Gson for serialization and deserialization.

## 🏛 Architecture

The application follows a servlet-based MVC architecture:

```
                       +-------------+
                       |   Browser   |
                       +------+------+
                              |
                              | HTTP Requests
                              |
                       +------v------+
                       |  Web Server |
                       | (Tomcat/etc)|
                       +------+------+
                              |
          +------------------+------------------+
          |                  |                  |
   +------v------+    +------v------+    +------v------+
   |             |    |             |    |             |
   |   Servlets  |    |  Filters    |    |  Listeners  |
   |             |    |             |    |             |
   +------+------+    +-------------+    +-------------+
          |
          |
   +------v------+
   |             |
   |   Models    |
   |             |
   +------+------+
          |
          |
   +------v------+
   |   JSON File |
   |   Storage   |
   |             |
   +-------------+
```

## 🔧 Technology Stack

### Backend
- **Language**: Java 17
- **Web**: Java Servlets 4.0, JSP
- **Server**: Apache Tomcat 9.0+
- **Data Storage**: JSON files
- **JSON Processing**: Google Gson
- **Authentication**: Session-based authentication
- **File Handling**: Java IO/NIO

### Frontend
- **HTML5/CSS3/JavaScript**
- **Bootstrap 5** for responsive design
- **jQuery** for DOM manipulation
- **AJAX** for asynchronous requests
- **Chart.js** for analytics

### Tools
- **Build Tool**: Maven/Gradle
- **Version Control**: Git
- **Testing**: JUnit, Mockito
- **IDE**: Eclipse/IntelliJ IDEA
- **Documentation**: JavaDoc
- **Logging**: Log4j/SLF4J

## 🚀 Core Features

### For Property Seekers
- **Agent Search**: Find agents by location, specialization, and ratings
- **Agent Profiles**: View detailed agent information and performance history
- **Appointment Scheduling**: Book meetings with selected agents
- **Manage Appointments**: View, reschedule, or cancel existing appointments
- **Favorites**: Save and compare preferred agents
- **Reviews & Ratings**: Rate agents after completed appointments

### For Real Estate Agents
- **Profile Management**: Update profile information and availability
- **Appointment Dashboard**: View and manage upcoming appointments
- **Calendar Management**: Set availability hours and blocked periods
- **Client Interaction**: Message system for communicating with clients
- **Performance Metrics**: View ratings and feedback statistics

### For Administrators
- **Agent Approval**: Review and approve agent registration requests
- **User Management**: Manage user accounts and permissions
- **System Configuration**: Configure system parameters and settings
- **Analytics**: View platform usage statistics and performance metrics
- **Content Management**: Update featured listings and announcements

## 📸 Screenshots

<div align="center">
  <img src="https://via.placeholder.com/400x250?text=Homepage" alt="Homepage" width="400"/>
  <img src="https://via.placeholder.com/400x250?text=Agent+Search" alt="Agent Search" width="400"/>
  <img src="https://via.placeholder.com/400x250?text=Agent+Profile" alt="Agent Profile" width="400"/>
  <img src="https://via.placeholder.com/400x250?text=Appointment+Booking" alt="Appointment Booking" width="400"/>
</div>

## 🚦 Getting Started

### Prerequisites
- JDK 17 or higher
- Apache Tomcat 9.0+ or other servlet container
- Maven or Gradle for building the project
- Git for version control
- IDE (Eclipse, IntelliJ IDEA, etc.)

### Local Development Setup

1. **Clone the repository**
```bash
git clone https://github.com/IT24103866/Real-State-Agent-Finder-and-Appointment-System.git
cd Real-State-Agent-Finder-and-Appointment-System
```

2. **Build the project**
```bash
# Using Maven
mvn clean install

# Using Gradle
gradle build
```

3. **Deploy to Tomcat**
```bash
# Copy the WAR file to Tomcat's webapps directory
cp target/realestate-agent-finder.war $CATALINA_HOME/webapps/
```

4. **Start Tomcat**
```bash
$CATALINA_HOME/bin/startup.sh  # Linux/Mac
%CATALINA_HOME%\bin\startup.bat  # Windows
```

5. **Access the application**
- Open your browser and navigate to: http://localhost:8080/realestate-agent-finder

### Initial Configuration

1. **Set up admin account**
- Navigate to http://localhost:8080/realestate-agent-finder/setup
- Create the initial administrator account

2. **Configure system settings**
- Log in as admin
- Navigate to Settings page
- Set up email templates, system parameters, etc.

## 💻 Development

### Project Building
```bash
# Clean and build
mvn clean install

# Run tests
mvn test

# Generate JavaDoc
mvn javadoc:javadoc
```

### Hot Deployment
For development with hot deployment:
1. Configure your IDE for Tomcat integration
2. Enable hot deployment in Tomcat (set `reloadable="true"` in context.xml)
3. Use IDE's deployment tools for quick updates

### JSON Data Files
The system stores data in the following JSON files:
- `users.json` - User account information
- `agents.json` - Agent profiles and details
- `appointments.json` - Appointment information
- `reviews.json` - Agent reviews and ratings
- `settings.json` - System configuration parameters

These files are stored in the application's data directory, configured in `config.properties`.

## 📚 API Reference

The application provides servlet-based endpoints accessible via HTTP requests.

### Authentication
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `POST /api/auth/register` - New user registration

### Agent API
- `GET /api/agents` - List all agents with filtering options
- `GET /api/agents/{id}` - Get specific agent details
- `POST /api/agents` - Create new agent (admin only)
- `PUT /api/agents/{id}` - Update agent information
- `DELETE /api/agents/{id}` - Delete agent (admin only)
- `GET /api/agents/{id}/availability` - Get agent availability slots

### Appointment API
- `GET /api/appointments` - List appointments for current user
- `GET /api/appointments/{id}` - Get appointment details
- `POST /api/appointments` - Create new appointment
- `PUT /api/appointments/{id}` - Update appointment
- `DELETE /api/appointments/{id}` - Cancel appointment
- `POST /api/appointments/{id}/confirm` - Confirm appointment

### Review API
- `GET /api/reviews/agent/{agentId}` - Get reviews for an agent
- `POST /api/reviews` - Submit a review
- `PUT /api/reviews/{id}` - Update a review
- `DELETE /api/reviews/{id}` - Delete a review

## 🚀 Deployment

### WAR Deployment
1. Build the WAR file:
```bash
mvn clean package
```

2. Deploy to servlet container:
- Copy `target/realestate-agent-finder.war` to Tomcat's `webapps` directory
- Start/restart Tomcat

### Production Considerations
- Ensure data directory has appropriate file permissions
- Configure regular backups of JSON data files
- Set up proper logging configuration
- Consider load balancing for higher traffic

### Configuration Parameters
Edit `config.properties` for production settings:
```properties
# Data storage location
data.directory=/var/lib/realestate-finder/data

# Log file path
log.file.path=/var/log/realestate-finder/app.log

# Maximum file size for agent photos (bytes)
max.photo.size=2097152

# Email notification settings
email.notifications.enabled=true
email.smtp.host=smtp.example.com
```

## 📂 Project Structure

```
src/
├── main/
│   ├── java/
│   │   └── com/
│   │       └── realestatefinder/
│   │           ├── config/        # Configuration classes
│   │           ├── controller/    # Servlet controllers
│   │           ├── filter/        # Request filters
│   │           ├── listener/      # Servlet context listeners
│   │           ├── model/         # Data models
│   │           │   ├── Agent.java
│   │           │   ├── Appointment.java
│   │           │   ├── Review.java
│   │           │   └── User.java
│   │           ├── service/       # Business logic
│   │           └── util/          # Utility classes
│   │               ├── JsonDataManager.java
│   │               └── ValidationUtils.java
│   ├── resources/
│   │   ├── config.properties      # Application configuration
│   │   └── log4j.properties       # Logging configuration
│   └── webapp/
│       ├── WEB-INF/
│       │   ├── web.xml            # Servlet configuration
│       │   └── jsp/               # JSP pages
│       ├── css/                   # Stylesheets
│       ├── js/                    # JavaScript files
│       └── images/                # Images and icons
└── test/
    └── java/
        └── com/
            └── realestatefinder/ # Test classes
```

## 🗺 Roadmap

### Q3 2023
- [ ] Mobile-responsive design improvements
- [ ] Email notification system
- [ ] Enhanced agent search filters

### Q4 2023
- [ ] In-app messaging between clients and agents
- [ ] Document sharing capabilities
- [ ] Calendar integration (iCal, Google Calendar)

### Q1 2024
- [ ] API for third-party integrations
- [ ] Advanced analytics dashboard
- [ ] Property listing integration

## 👥 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please read our [Contributing Guidelines](CONTRIBUTING.md) for more details.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">
  <p>
    <sub>© 2023-2025 Real Estate Agent Finder and Appointment System</sub>
  </p>
  <sub>Last updated: 2025-05-18</sub>
</div>
