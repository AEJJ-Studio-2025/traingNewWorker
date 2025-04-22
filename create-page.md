## How to Add a Page

## Menu

1. [Step 1: Create a New Branch and Clone the Repository](#step-1-create-a-new-branch-and-clone-the-repository)
2. [Step 2: Copy the Database File into the New Branch](#step-2-copy-the-database-file-into-the-new-branch)
3. [Step 3: Initialize the Server](#step-3-initialize-the-server)
4. [Step 4: Start the Application](#step-4-start-the-application)
5. [Step 5: Modify the Application Files](#step-5-modify-the-application-files)
6. [Step 6: Register the Application in Settings](#step-6-register-the-application-in-settings)
7. [Step 7: Run Migrations and Start the Server](#step-7-run-migrations-and-start-the-server)

---

## Step 1: Create a New Branch and Clone the Repository

1. **Create a new branch** from the `main` branch on GitHub.
   - This allows you to isolate your changes and work without affecting the main production code.

2. **Clone the repository using SSH**:
   ```bash
   git clone git@github.com:AEJJ-Studio-2025/laiyff-web-dev.git
   ```
   - `git clone`: Copies the entire project to your computer.
   - The SSH URL ensures secure access without typing your GitHub password repeatedly.

---

## Step 2: Copy the Database File into the New Branch

1. **Clone the working branch repo** (if you haven’t already):
   ```bash
   git clone -b edward-db-practice git@github.com:EDYBIRD/wagtail-dev-practice.git
   ```
   - `-b edward-db-practice`: Tells Git to check out the specified branch after cloning.
   - Useful if your work is in a development branch and not `main`.

2. **Copy the compressed database file into the repository**:
   ```bash
   cp ddd.7z laiyff-web-dev/
   ```
   - `cp`: The Unix `copy` command.
   - Copies the compressed file (`ddd.7z`) into the cloned folder `laiyff-web-dev/`.

3. **Decompress the database using `7za`**:
   ```bash
   7za d ddd.7z db.20250222 -p<your-password>
   ```
   - `7za`: 7-Zip command-line tool.
   - `d`: Extracts the content from the archive.
   - `-p<your-password>`: Use the password to decrypt the archive.

---

## Step 3: Initialize the Server

1. **Go to the scripts folder** that contains setup scripts:
   ```bash
   cd laiyff-web-dev/utilScripts
   ```
   - `cd`: Change directory.
   - This step puts you in the folder where utility/setup scripts are located.

2. **Run the initialization script**:
   ```bash
   ./initialEnv.sh
   ```
   - `./initialEnv.sh`: Executes the script in the current folder.
   - This typically sets up your Python virtual environment, installs dependencies, and loads environment variables.

---

## Step 4: Start the Application

1. **Make sure you’re in the `utilScripts` directory**:
   ```bash
   cd laiyff-web-dev/utilScripts
   ```
   - Just in case you navigated away—this ensures you're in the right folder to execute the next script.

2. **Run the script to create a new app**:
   ```bash
   ./startApp myApp1
   ```
   - This command creates a new Django/Wagtail app called `myApp1`.
   - You’ll later define models and templates in this app.

---

## Step 5: Modify the Application Files

1. **Open the app folder in VS Code**:
   ```bash
   code laiyff-web-dev/myApp1
   ```
   - Launches VS Code in the app directory so you can edit files easily.

2. **Edit `models.py`**:
   - Define your Wagtail page models using Django’s model system.
   - Example:
     ```python
     from wagtail.models import Page
     class CustomPage(Page):
         pass
     ```

3. **Create a CSS file** in `static/css/`:
   - Add your own styles here that will be used in your HTML templates.

4. **Create an HTML file** in `templates/myApp1/`:
   - Wagtail uses these templates to render pages created in the CMS.
   - Example:
     ```html
     {% extends "base.html" %}
     {% block content %}
       <h1>{{ page.title }}</h1>
     {% endblock %}
     ```

---

## Step 6: Register the Application in Settings

1. **Open and edit `base.py` in `YourWebsiteNameMain/settings/`**:
   - This file controls Django’s settings.

2. **Add the new app to `INSTALLED_APPS`**:
   ```python
   INSTALLED_APPS = [
       ...
       'myApp1',
   ]
   ```
   - Django needs this entry to recognize and include your app.

---

## Step 7: Run Migrations and Start the Server

1. **Navigate to the utility script directory**:
   ```bash
   cd laiyff-web-dev/utilScripts
   ```

2. **Generate migration files**:
   ```bash
   ./makeMigrations.sh
   ```
   - Detects any model changes you made and creates migration files.

3. **Run the Django development server**:
   ```bash
   ./runWebsite.sh
   ```
   - Starts the local server so you can view the website at:
     ```
     http://localhost:8000/
     ```

---

After everything is running, visit:
```
http://localhost:8000/admin/
```
Log in with your admin credentials and test your newly created page model by adding it under the "Pages" section.

