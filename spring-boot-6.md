#### 1. **What is Spring Boot?**

* An **opinionated framework** built on top of Spring.
* Simplifies Spring app setup by providing **auto-configuration** and **starter dependencies**.
* Comes with an **embedded server** (Tomcat, Jetty) so you don’t need to deploy WAR files.
* Focuses on **convention over configuration** to reduce boilerplate.

---

#### 2. **Key Features**

* **Auto-configuration:** Automatically configures beans based on classpath and properties.
* **Starter POMs:** Predefined dependency sets (`spring-boot-starter-web`, `spring-boot-starter-data-jpa`, etc.)
* **Embedded servers:** Runs apps as standalone JARs with embedded Tomcat or others.
* **Actuator:** Provides production-ready features like health checks and metrics.
* **Spring Boot CLI:** Command line tool for quick app prototyping.

---

#### 3. **Main Components**

* `@SpringBootApplication` — combination of `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`.
* **Application Runner:** Contains the main method to launch the app with `SpringApplication.run()`.
* Configuration via **application.properties** or **application.yml** files.

---

#### 4. **How does Auto-configuration work?**

* Looks for **classes and properties** on the classpath.
* Configures beans automatically when it detects necessary classes.
* You can override with your own `@Bean` definitions or configuration files.

---

#### 5. **Spring Boot Starter POMs**

* `spring-boot-starter-web`: For building web apps, REST APIs.
* `spring-boot-starter-data-jpa`: For JPA and Hibernate support.
* `spring-boot-starter-security`: For Spring Security.
* Others for testing, mail, batch processing, etc.

---

#### 6. **Spring Boot Actuator**

* Adds endpoints like `/actuator/health`, `/actuator/metrics` for monitoring.
* Helps with app health, metrics, auditing, etc.

---

#### 7. **How to run a Spring Boot app?**

* Use `mvn spring-boot:run` or `java -jar yourapp.jar`.
* Runs as standalone with embedded server.

---

#### 8. **Profiles and Configurations**

* Supports multiple **profiles** (`dev`, `prod`, `test`).
* Configurations can be environment-specific in `application-{profile}.properties`.
