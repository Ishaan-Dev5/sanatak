# 📄 Understanding `pom.xml` in Maven

---

## 🔍 What is `pom.xml`?

`pom.xml` stands for **Project Object Model**, and it's the core configuration file used by **Apache Maven**, a popular build automation tool for Java projects.

It tells Maven:
- How to build your project
- What dependencies (libraries) are needed
- Project metadata (name, version, description)
- Build plugins and goals

---

## ❓ Why is `pom.xml` Important?

| Reason                   | Explanation                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Dependency Management** | Automatically downloads required libraries and manages transitive dependencies. |
| **Build Lifecycle**      | Defines how your code is compiled, tested, packaged, and deployed.         |
| **Project Metadata**     | Stores version, authorship, licensing, and module info.                     |
| **Plugin Configuration** | Integrates tools like Surefire (tests), Checkstyle (linting), Shade (uber-jar). |
| **Standardization**      | Promotes consistency across teams and projects.                            |

---

## 🧰 Use Cases

| Use Case                          | Description                                                         |
|----------------------------------|---------------------------------------------------------------------|
| **Java Web Application**         | Build and manage web apps using Servlet APIs, Spring, etc.          |
| **Microservices (Spring Boot)**  | Manage multiple microservices with clear dependency boundaries.     |
| **Library/SDK Projects**         | Create reusable Java libraries for internal or public distribution. |
| **CI/CD Pipelines**              | Automate build, test, and deployment with Jenkins/GitHub Actions.   |
| **Multi-module Projects**        | Organize large codebases with parent/child `pom.xml` structure.     |

---

## 📦 Defining Dependencies

Dependencies are added in the `<dependencies>` section:

```xml
<dependencies>
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>3.1.1</version>
  </dependency>
</dependencies>
