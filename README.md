# Dev Challenge Test Automation
Project Structure

1. Project Directory
   dev-challenge-automation/
├── tests/
│   ├── test_contact_email.py
│   ├── test_count_judges.py
│   └── test_no_mobile_partners.py
├── requirements.txt
├── README.md
└── .github/
    └── workflows/
        └── ci.yml

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

**Running the Tests**
To run the tests, execute the following command in the terminal:
pytest tests/

** Test Cases Implementation**

test_contact_email.py

from selenium import webdriver
from selenium.webdriver.common.by import By

def test_contact_email():
    driver = webdriver.Chrome()
    driver.get("https://www.devchallenge.it")
    driver.find_element(By.LINK_TEXT, "DEV Challenge").click()
    driver.find_element(By.LINK_TEXT, "About").click()
    driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
    
    email = driver.find_element(By.XPATH, "//*[contains(text(), 'hello@devchallenge.it')]")
    assert email.is_displayed()
    driver.quit()

test_count_judges.py

from selenium import webdriver
from selenium.webdriver.common.by import By

def test_count_judges():
    driver = webdriver.Chrome()
    driver.get("https://www.devchallenge.it")
    driver.find_element(By.LINK_TEXT, "DEV Challenge").click()
    driver.find_element(By.LINK_TEXT, "Judges").click()

    judges = driver.find_elements(By.CLASS_NAME, "judge")  # Update with the actual class name
    assert len(judges) == 6
    driver.quit()

test_no_mobile_partners.py

from selenium import webdriver
from selenium.webdriver.common.by import By

def test_no_mobile_partners():
    options = webdriver.ChromeOptions()
    options.add_argument("window-size=360,800")
    driver = webdriver.Chrome(options=options)
    
    driver.get("https://www.devchallenge.it")
    driver.find_element(By.LINK_TEXT, "DEV Challenge").click()
    driver.find_element(By.LINK_TEXT, "Partners").click()

    partners = driver.find_elements(By.CLASS_NAME, "partner")  # Update with the actual class name
    assert not any(partner.text == "Apple Inc" for partner in partners)
    driver.quit()
    
    **Requirements File**
    requirements.txt
    selenium


**CI/CD Configuration**
The project includes a CI/CD pipeline configuration in .github/workflows/ci.yml.

### 4. CI/CD Configuration

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


**Step-by-Step Guide to Set Up the Project on GitHub**
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




