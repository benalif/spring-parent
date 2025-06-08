# Maven Parent POM - GitHub Packages

This project defines a reusable **parent POM** to centralize dependency management, plugin versions, and common configurations for Maven-based projects. It is published to **GitHub Packages** to be used across multiple repositories.

## 🧱 Project Structure

This repository contains only a `pom.xml` file with `<packaging>pom</packaging>`, designed to be used as a parent in other Maven projects.

## 📦 GitHub Packages

The parent POM is published to GitHub Packages. Other projects can include it as their parent like so:

```xml
<parent>
  <groupId>com.yourorg</groupId>
  <artifactId>parent-pom</artifactId>
  <version>1.0.0</version>
</parent>
```
Add the following to your ~/.m2/settings.xml or project-level pom.xml:
```xml
<repositories>
  <repository>
    <id>github</id>
    <url>https://maven.pkg.github.com/your-github-username/parent-pom-repo</url>
  </repository>
</repositories>
 ```
And in settings.xml, configure authentication:
```xml
<servers>
  <server>
    <id>github</id>
    <username>YOUR_GITHUB_USERNAME</username>
    <password>YOUR_GITHUB_TOKEN</password>
  </server>
</servers>
```
🔐 Use a GitHub personal access token (PAT) with read:packages, write:packages, and repo scopes for private repositories.

# 🚀 Publishing

To publish the POM to GitHub Packages:

Make sure you're authenticated via your ~/.m2/settings.xml.

Run:
```xml
mvn clean deploy
```
Make sure your pom.xml includes:
```xml
<distributionManagement>
  <repository>
    <id>github</id>
    <url>https://maven.pkg.github.com/your-github-username/parent-pom-repo</url>
  </repository>
</distributionManagement>
```
And that your POM is marked as a parent:
```xml
<packaging>pom</packaging>
```
# 📁 Example POM Structure
```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.yourorg</groupId>
  <artifactId>parent-pom</artifactId>
  <version>1.0.0</version>
  <packaging>pom</packaging>

  <modules />
  
  <dependencyManagement>
    <dependencies>
      <!-- common dependencies -->
    </dependencies>
  </dependencyManagement>

  <build>
    <pluginManagement>
      <plugins>
        <!-- shared plugin config -->
      </plugins>
    </pluginManagement>
  </build>

  <distributionManagement>
    <repository>
      <id>github</id>
      <url>https://maven.pkg.github.com/your-github-username/parent-pom-repo</url>
    </repository>
  </distributionManagement>
</project>
```
