Here's a concise summary of the CI/CD pipeline setup using GitHub Actions for a Node.js app with Docker:

### **Key Steps Summary:**
1. **Create Node.js App**  
   - Simple Express server with basic test (Mocha).
   - `package.json` configured with `test` and `start` scripts.

2. **Dockerize the App**  
   - `Dockerfile` uses `node:16-alpine` for lightweight builds.  
   - `.dockerignore` excludes unnecessary files.

3. **GitHub Repository Setup**  
   - Push code to GitHub (triggers workflow on `main` branch).

4. **GitHub Actions Workflow**  
   - **Two Jobs:**  
     - **Test:** Runs on Ubuntu, installs dependencies, executes tests.  
     - **Build & Deploy:**  
       - Builds Docker image using Buildx (multi-arch support).  
       - Pushes to Docker Hub with `latest` and Git commit SHA tags.  
   - **Secrets:** Stores `DOCKER_HUB_USERNAME` and `DOCKER_HUB_TOKEN` securely.

5. **Amazon Linux Compatibility**  
   - Workflow runs on GitHub’s Ubuntu runners by default.  
   - Optional: Add a job to test specifically on Amazon Linux container.

6. **Trigger & Monitor**  
   - Pipeline runs automatically on `git push` to `master`.  
   - View progress in GitHub’s **Actions** tab.

### **Outcome:**
- **Automated:** Tests, builds, and deploys on every push.  
- **Reliable:** Uses modern tools (Node 16, Docker Buildx).  
- **Scalable:** Ready for cloud deployment (e.g., AWS ECS/EC2).

<img width="1920" height="932" alt="Screenshot (236)" src="https://github.com/user-attachments/assets/5349f35f-dbf4-4fec-b70a-ac415d995820" />
<img width="1920" height="824" alt="Screenshot (96)" src="https://github.com/user-attachments/assets/b4a0936d-2624-4efe-9f13-1943f17e4bb9" />


### **Troubleshooting Tips:**
- Ensure Docker Hub secrets are correctly set in GitHub.  
- Check YAML syntax and file paths.  
- Use `npx mocha` for consistent test execution.  

This pipeline ensures **code quality** (via tests) and **consistent deployments** (via Docker) with minimal manual effort. 🚀
Note: In build and push I got error because of username
