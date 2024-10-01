# Dev Challenge Test Automation

## Overview
This project contains automated tests for the Dev Challenge website using Selenium.

## Pre-requisites
1. **Operating System**: Windows
2. **Install Python**: [Download and install Python](https://www.python.org/downloads/)
3. **Install Chrome**: [Download and install Chrome](https://www.google.com/chrome/)
4. **Install ChromeDriver**: Ensure ChromeDriver is in your PATH or specify its location in the script.
5. **Install dependencies**: Run the following command:
   ```bash
   pip install -r requirements.txt


**CI/CD Configuration**
The project includes a CI/CD pipeline configuration in .github/workflows/ci.yml.
Step-by-Step Guide to Set Up the Project on GitHub
1. Create a GitHub Account: If you haven't already, sign up for a GitHub account.

2. Create a New Repository:

- Go to your GitHub profile and click on "Repositories."
- Click the "New" button to create a new repository.
- Name it dev-challenge-automation.

3. Clone the Repository:

git clone https://github.com/yourusername/dev-challenge-automation.git
cd dev-challenge-automation

4. Add the Files: Create the directory structure and files as outlined above. Use your preferred code editor.

5. Commit and Push:

git add .
git commit -m "Initial commit for test automation project"
git push origin main

6. Verify the CI/CD: After pushing, check the "Actions" tab on your repository to see if the workflow runs successfully.

**Final Steps**
-Make sure to test everything locally before pushing to ensure all tests pass.
-Double-check that no personal information is included in your code or README file.
-Archive your project as a ZIP file to submit it according to the challenge guidelines.


#### `.github/workflows/ci.yml`
```yaml
name: CI

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.8'

    - name: Install dependencies
      run: |
        pip install -r requirements.txt

    - name: Run tests
      run: |
        pytest tests/

