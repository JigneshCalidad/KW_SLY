# Module 11: Jenkins CI/CD

## 🌱 Why This Module Matters

Jenkins isn't just a tool—it's a **philosophy of continuous integration**. It represents the shift from "run tests manually" to "tests run automatically, continuously, reliably."

Understanding Jenkins enables you to:
- Automate test execution
- Integrate testing into development workflow
- Provide continuous feedback
- Scale test execution

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **Jenkins Introduction** - What CI/CD is and why it matters
2. **Jenkins Setup** - Installing and configuring
3. **Running Java Programs** - Basic job configuration
4. **Running Selenium Scripts** - Test automation integration
5. **Reports and Notifications** - Getting test results

---

## 🧩 Conceptual Overview

### Introduction to Jenkins

**What Jenkins is**: Open-source automation server for CI/CD.

**CI/CD Concepts**:
- **Continuous Integration (CI)**: Automatically build and test on code changes
- **Continuous Deployment (CD)**: Automatically deploy to environments

**Benefits**:
- **Automation**: No manual test execution
- **Early feedback**: Catch issues quickly
- **Consistency**: Same environment every run
- **History**: Track results over time
- **Notifications**: Alert on failures

**Philosophy**: "If it's manual, automate it."

---

### Jenkins Setup

**Installation**:
1. Download Jenkins (war file or installer)
2. Run: `java -jar jenkins.war`
3. Access: `http://localhost:8080`
4. Complete setup wizard

**Initial setup**:
- Install suggested plugins
- Create admin user
- Configure URL

**Plugins needed**:
- Maven Integration
- Git Plugin
- TestNG Results Plugin
- HTML Publisher (for reports)

---

### Running a Normal Java Program

**Basic job**:
1. **New Item** → **Freestyle project**
2. **Configure**:
   - Source Code Management: Git (if needed)
   - Build: Execute shell/Windows batch
     ```bash
     javac HelloWorld.java
     java HelloWorld
     ```
3. **Build Now**

**Concepts**:
- **Job**: Configuration for a task
- **Build**: Execution of a job
- **Console Output**: Logs from execution

---

### Running Selenium Scripts

**Configuration**:

1. **Source Code Management**:
   - Git repository URL
   - Credentials (if private)

2. **Build Triggers**:
   - **Poll SCM**: Check for changes periodically
   - **Build periodically**: Run on schedule
   - **Triggered by other projects**: Chain jobs

3. **Build**:
   ```bash
   mvn clean test
   ```
   Or if using TestNG:
   ```bash
   mvn test -DsuiteXmlFile=testng.xml
   ```

4. **Post-build Actions**:
   - **Publish TestNG Results**: `test-output/testng-results.xml`
   - **Publish HTML reports**: Test reports folder
   - **Email notifications**: On failure/success

**Advanced**:
- **Parameterized builds**: Pass parameters to tests
- **Parallel execution**: Run tests in parallel
- **Matrix builds**: Test on multiple configurations

---

### Reports and Notifications

**TestNG Reports**:
- Plugin publishes test results
- Shows pass/fail, trends
- Links to detailed reports

**HTML Reports**:
- Custom reports (Extent, Allure)
- Visual test results
- Screenshots, logs

**Email Notifications**:
- Configure SMTP
- Send on failure/success
- Include test results

**Slack/Teams Integration**:
- Notify team channels
- Real-time updates

---

### Best Practices

1. **Version control**: Store Jenkinsfile in Git
2. **Pipeline as Code**: Use Jenkinsfile (declarative/scripted)
3. **Clean workspace**: Clean before each build
4. **Artifact archiving**: Save test reports, screenshots
5. **Failure handling**: Notify appropriately
6. **Security**: Manage credentials properly

---

## 🎯 Key Takeaways

1. **Jenkins automates execution** - Tests run automatically
2. **CI/CD integrates testing** - Part of development workflow
3. **Reports provide feedback** - Visualize test results
4. **Notifications keep team informed** - Real-time updates
5. **Scalability** - Run tests on multiple machines

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 5**: GIT provides source code
- **Module 8**: TestNG provides test execution
- **Module 9**: Frameworks provide test structure
- **Module 10**: Maven provides build management

---

**Reflection Question**: How does CI/CD change the role of testing from "something we do" to "something that happens automatically"?

