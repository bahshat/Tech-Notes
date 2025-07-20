Here are detailed, concise **Jenkins interview notes** to help you revise quickly and effectively:

---

## 🔧 Jenkins Interview Notes

### 1. **What is Jenkins?**

* Open-source automation server for building, testing, and deploying software.
* Widely used in CI/CD pipelines.
* Highly extensible with plugins (Git, Docker, Kubernetes, Slack, etc.).

---

### 2. **Key Concepts**

| Concept        | Description                                    |
| -------------- | ---------------------------------------------- |
| **Job**        | Unit of work in Jenkins (e.g., build or test)  |
| **Pipeline**   | Scripted/Declarative set of stages and steps   |
| **Agent/Node** | Machine where jobs run                         |
| **Executor**   | Slot to run a job on a node                    |
| **Workspace**  | Directory for job files during execution       |
| **Artifact**   | Output of a job (e.g., build files)            |
| **Trigger**    | Automatic job start (SCM webhook, timer, etc.) |

---

### 3. **Types of Jobs**

* Freestyle Project
* Pipeline (Scripted or Declarative)
* Multibranch Pipeline (for GitHub repos)
* External jobs (for monitoring processes outside Jenkins)

---

### 4. **Jenkins Pipeline Example (Declarative)**

```groovy
pipeline {
  agent any
  environment {
    ENV = "staging"
  }
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/user/repo.git'
      }
    }
    stage('Build') {
      steps {
        sh 'make build'
      }
    }
    stage('Test') {
      steps {
        sh 'make test'
      }
    }
    stage('Deploy') {
      when {
        branch 'main'
      }
      steps {
        sh './deploy.sh'
      }
    }
  }
}
```

---

### 5. **Triggers**

* **SCM Polling:** Periodically checks for changes in source control.
* **Webhooks:** GitHub/GitLab push triggers build.
* **Timer:** `@daily`, `H/5 * * * *`, etc. (CRON syntax)

---

### 6. **Artifacts**

* Stored build outputs.

```groovy
archiveArtifacts artifacts: 'build/*.zip', fingerprint: true
```

---

### 7. **Post Actions**

* Run actions regardless of build status.

```groovy
post {
  success {
    echo "Build succeeded"
  }
  failure {
    mail to: 'dev@example.com', subject: 'Build Failed'
  }
}
```

---

### 8. **Credentials Management**

* Store SSH keys, passwords, tokens securely.
* Access via `withCredentials` block.

---

### 9. **Jenkinsfile (Pipeline as Code)**

* Stored in the root of the repository (`Jenkinsfile`)
* Enables version control of CI logic
* Helps in repeatable & auditable builds

---

### 10. **Common Plugins**

* Git
* Pipeline
* Blue Ocean (UI)
* Docker/Docker Pipeline
* Slack Notification
* Kubernetes (Jenkins on K8s)

---

### 11. **Distributed Builds**

* Master/Agent setup
* Agent can be physical or cloud VMs, containers
* SSH or JNLP agents
* Useful for scaling or platform-specific builds

---

### 12. **Best Practices**

* Use Pipelines instead of Freestyle jobs
* Use parallel stages for faster builds
* Isolate credentials from code
* Archive and fingerprint artifacts
* Use post actions for cleanup or notifications

---

### 13. **Interview Questions**

* Difference between scripted and declarative pipelines?
* How do you trigger a Jenkins job from GitHub?
* How do you pass environment variables between stages?
* How to reuse steps between pipelines?
* What’s the difference between `agent none` and `agent any`?
* How do you run Jenkins in Docker?
* How do you scale Jenkins?

---

Ready to move on to the **Git** section next?
