## How to add a page

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

1. **Create a new branch** from `main` on GitHub.
2. **Clone the repository using SSH**:
   ```bash
   git clone git@github.com:AEJJ-Studio-2025/laiyff-web-dev.git
   ```
   -Be to choose **SSH** when cloning.

---

## Step 2: Copy the Database File into the New Branch

1. **Clone the repository with the new branch**:
   ```bash
   git clone -b edward-db-practice git@github.com:EDYBIRD/wagtail-dev-practice.git
   ```

2. **Copy the compressed database file into the repository folder**:
   ```bash
   cp ddd.7z laiyff-web-dev/
   ```
   > 🔎 **Note**: The file name might not be `ddd.7z`; it could be `db.20250222.7z` or something else. Double-check the actual file name before copying.
3. **Decompress the database file** using `7za`:
   ```bash
   7za d ddd.7z db.20250222 -p<your-password>
   ```

---

## Step 3: Initialize the Server

1. **Navigate to the `utilScripts` directory**:
   ```bash
   cd laiyff-web-dev/utilScripts
   ```

2. **Run the initialization script**:
   ```bash
   ./initialEnv.sh
   ```

---

## Step 4: Start the Application

1. **Ensure you're still in the `utilScripts` directory**:
   ```bash
   cd laiyff-web-dev/utilScripts
   ```

2. **Run the script to start the application** (script name might be something like `startApp`):
   ```bash
   ./startApp myApp1
   ```

---

## Step 5: Modify the Application Files

1. **Open your app folder in VS Code**:
   ```bash
   code <your-app-folder-name>
   ```

2. **Edit `models.py`** in your `myApp1` folder:
   - Define your data models.

3. **Create a CSS file** in the `static/css/` folder:
   - Add custom styles for your page.

4. **Create an HTML file** in the `myApp1\templates` folder:
   - Add your basic HTML layout and structure.

---

## Step 6: Register the Application in Settings

1. **Edit the `base.py` file** located in `YourWebsiteNameMain/settings/`:
   - Add your app to the `INSTALLED_APPS` list:
   ```python
   INSTALLED_APPS = [
       ...
       'myApp1,
   ]
   ```

---

## Step 7: Run Migrations and Start the Server

1. **Navigate to the `utilScripts` directory**:
   ```bash
   cd laiyff-web-dev/utilScripts
   ```

2. **Run migrations**:
   ```bash
   ./makeMigrations.sh
   ```

3. **Start the server**:
   ```bash
   ./runWebsite.sh
   ```

---