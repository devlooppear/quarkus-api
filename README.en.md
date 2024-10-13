# 🛠️ Quarkus API

This project uses **Quarkus**, the **Supersonic** and **Subatomic** Java framework.

![Quarkus](https://img.shields.io/badge/Quarkus-v2.6.0-orange?style=flat-square)
![Java](https://img.shields.io/badge/Java-17-brightgreen?style=flat-square)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?style=flat-square)

## 🌟 What is Quarkus?

Quarkus is a framework designed to simplify the creation of Java applications optimized for cloud environments and microservices. It stands out for its **fast startup** and **lower memory consumption**, making it ideal for native applications in containers.

That's why I created a base for my future projects, making the configuration more accessible by combining `.env` and `src/main/resources/application.properties`. This way, I can better protect environment variables and easily switch between environments like **dev**, **prod**, and **test**.

I also included a **Docker Compose** file so you can easily set up any Dockerfile you want created by Quarkus. Additionally, I configured a simplified environment for REST APIs, including **JPA** and **Hibernate** libraries for ORM, and **Lombok** to avoid writing a ton of getters and setters. Hahahah.

I found Quarkus to be really cool, and I hope you enjoy it too! When I start a project, it can be somewhat complicated, so I like to set up a good development environment first. I imagine many people go through the same process, which is why I created this project and am trying to make the documentation very accessible.

### 🚀 Key Advantages of Quarkus Over Spring Boot

- **Performance**: Faster startup and reduced memory usage.
- **Native Compilation**: Support for GraalVM to create native executables that further enhance performance.
- **Live Coding**: Development mode that allows you to see code changes in real time without restarting the application.
- **Ease of Integration**: Extensions for easily connecting to databases, REST services, and more.

## 🛠️ Running the Application in Development Mode

Before running the application, copy the example environment variables file to a new `.env` file. You can do this with the following command:

```bash
cp .env.example .env
```

Then, to run your application in development mode with live coding enabled, use:

```bash
./mvnw compile quarkus:dev
```

After starting the application, you can access it at http://localhost:8080/hello.

NOTE: Quarkus now includes a Dev UI, which is available only in development mode at http://localhost:8080/q/dev/.

📦 Packaging and Running the Application
The application can be packaged using:

```bash
./mvnw package
```

This produces the quarkus-run.jar file in the target/quarkus-app/ directory. You can run the application using:

```bash
java -jar target/quarkus-app/quarkus-run.jar
```

If you want to create an über-jar, execute the following command:

```bash
./mvnw package -Dquarkus.package.jar.type=uber-jar
```

The application packaged as an über-jar can be executed with:

```bash
java -jar target/*-runner.jar
```

🥇 Creating a Native Executable
You can create a native executable using:

```bash
./mvnw package -Dnative
```

Or, if you don't have GraalVM installed, you can build the native executable in a container:

```bash
./mvnw package -Dnative -Dquarkus.native.container-build=true
```

The native executable can be run with:

```bash
./target/quarkus-api-1.0.0-SNAPSHOT-runner
```

For more information on creating native executables, please refer to the Quarkus documentation.

## 🚀 Running the Application

To execute the application, use:

```bash
./mvnw quarkus:dev
```

## 🐳 Dockerfiles

In the src/main/docker directory, you will find several Dockerfiles that facilitate the packaging and execution of your Quarkus application:

### 📦 Available Dockerfiles:

- **`Dockerfile.jvm`**:  
  For running the application on the JVM, ideal for developers who prefer the standard execution.

- **`Dockerfile.legacy-jar`**:  
  For applications that require the use of legacy JARs.

- **`Dockerfile.native`**:  
  For building a native image with GraalVM, providing better performance and shorter startup times.

- **`Dockerfile.native-micro`**:  
  Ideal for microservices, optimizing the image to be lightweight and efficient.

## ⚙️ Database Configuration

For more information on how to configure the PostgreSQL database, check the following guides:

- **[Hibernate ORM with Panache](https://quarkus.io/guides/hibernate-orm-panache)**: Simplify your persistence code with Hibernate ORM.
- **[JDBC Driver - PostgreSQL](https://quarkus.io/guides/datasource)**: Connect to the PostgreSQL database via JDBC.
- **[RESTEasy Classic](https://quarkus.io/guides/resteasy)**: Framework for implementing REST services.

## 📚 Provided Code

- **Hibernate ORM**: Create your first JPA entity. [More information](https://quarkus.io/guides/hibernate-orm).
- **RESTEasy JAX-RS**: Easily start your RESTful services. [More information](https://quarkus.io/guides/resteasy).


## 🧹 Cleaning and Running

Note: If you change the configurations, you may need to run:

```bash
./mvnw clean
```
