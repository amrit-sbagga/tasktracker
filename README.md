# Task Tracker

Spring Boot project for building a task tracker REST API.

## Stack

- Java 21
- Spring Boot 4.0.6
- Spring Web MVC
- Spring Data JPA
- PostgreSQL
- Maven (via wrapper — no separate Maven install required)

## Prerequisites

1. **JDK 21**

   ```bash
   brew install openjdk@21
   java -version
   ```

2. **PostgreSQL** (when you connect the app to a database)

   Configure connection settings in `src/main/resources/application.properties`.

## Setup

Clone or open this project, then install dependencies from the project root:

```bash
cd tasktracker
./mvnw dependency:resolve
```

Or compile the project (downloads dependencies and builds):

```bash
./mvnw clean compile
```

Dependencies are stored in your local Maven cache (`~/.m2/repository`).

## Common Maven Commands

Use `./mvnw` (Maven Wrapper) instead of `mvn` so the project always uses the correct Maven version.

| Command | Description |
|---------|-------------|
| `./mvnw dependency:resolve` | Download and resolve all dependencies |
| `./mvnw clean compile` | Clean build output and compile the project |
| `./mvnw test` | Run unit tests |
| `./mvnw spring-boot:run` | Start the application |
| `./mvnw clean package` | Build a runnable JAR in `target/` |

### Examples

```bash
# First-time setup
./mvnw clean compile

# Run tests
./mvnw test

# Start the app (default port 8080)
./mvnw spring-boot:run

# Build JAR
./mvnw clean package
java -jar target/tasktracker-0.0.1-SNAPSHOT.jar
```

## Cursor / VS Code Setup

Recommended extensions:

- **Extension Pack for Java** (Microsoft) — language support, debugger, Maven integration
- **Spring Boot Extension Pack** (VMware) — Spring Boot tools and dashboard

After installing, open this folder and let Cursor import the Maven project. If needed:

- `Cmd+Shift+P` → **Java: Import Java Projects in Workspace**

## Project Structure

```
tasktracker/
├── pom.xml                          # Maven config and dependencies
├── mvnw                             # Maven wrapper (Unix/macOS)
├── src/main/java/com/tasktracker/   # Application source code
├── src/main/resources/              # Config (application.properties)
└── src/test/java/                   # Tests
```

## References

See [HELP.md](./HELP.md) for Spring Boot and Maven documentation links.
