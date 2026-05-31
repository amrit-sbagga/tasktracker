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

2. **PostgreSQL** — running locally with a database named `tasktracker`

   ```sql
   CREATE DATABASE tasktracker;
   ```

## First-time setup

From the project root:

```bash
cd tasktracker

# 1. Install dependencies
./mvnw clean compile

# 2. Create local config from the example template
cp src/main/resources/application-local.properties.example \
   src/main/resources/application-local.properties

# 3. Edit application-local.properties with your PostgreSQL username and password

# 4. Start the app (default port 8080)
./mvnw spring-boot:run
```

## Configuration

Database credentials are kept out of git using Spring's `local` profile.

| File | Committed? | Purpose |
|------|------------|---------|
| `src/main/resources/application.properties` | Yes | App name, JPA settings, activates `local` profile |
| `src/main/resources/application-local.properties.example` | Yes | Template — copy this to get started |
| `src/main/resources/application-local.properties` | **No** (gitignored) | Your real DB URL, username, and password |

**`application.properties`** (shared, safe to commit):

```properties
spring.application.name=tasktracker
spring.profiles.active=local
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

**`application-local.properties`** (local only — never commit):

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/tasktracker
spring.datasource.username=postgres
spring.datasource.password=your_password
```

On a fresh clone, copy the example file again and fill in your credentials. The app will not connect to PostgreSQL without `application-local.properties`.

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
# Run tests
./mvnw test

# Start the app (requires application-local.properties)
./mvnw spring-boot:run

# Build and run JAR
./mvnw clean package
java -jar target/tasktracker-0.0.1-SNAPSHOT.jar
```

Dependencies are stored in your local Maven cache (`~/.m2/repository`).

## Cursor / VS Code Setup

Recommended extensions:

- **Extension Pack for Java** (Microsoft) — language support, debugger, Maven integration
- **Spring Boot Extension Pack** (VMware) — Spring Boot tools and dashboard

After installing, open this folder and let Cursor import the Maven project. If needed:

- `Cmd+Shift+P` → **Java: Import Java Projects in Workspace**

## Project Structure

```
tasktracker/
├── pom.xml
├── mvnw
├── src/main/java/com/tasktracker/          # Application source code
├── src/main/resources/
│   ├── application.properties              # Shared config (committed)
│   ├── application-local.properties.example # DB config template (committed)
│   └── application-local.properties        # Local secrets (gitignored)
└── src/test/java/                          # Tests
```

## References

See [HELP.md](./HELP.md) for Spring Boot and Maven documentation links.
