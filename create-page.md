## How to add a page
## Step 1: Create a New Branch and Clone the Repository

1. **Create a new branch** under `main` on GitHub.
2. **Clone the repository** using SSH:
   ```bash
   git clone the code and within there chose the ssh


## Step 2: Copy the Database File into the New Branch

1. **Compress the database file** using `7za`:
   ```bash
   7za a ddd.7z db.20250222 -paswordxxxxxxx
   ```
2. **Clone the repository with the new branch**:
   ```bash
   git clone -b edward-db-practice git@github.com:EDYBIRD/wagtail-dev-practice.git
   ```
3. **Copy the compressed database file into the repository folder**:
   ```bash
   cp ddd.7z wagtail-dev-practice/
   
for part 3 of step2, the file might not be ddd.7z, it could be db.20250222 so just becareful and remember the file name you named.

## Step 3: Initialize the Server

1. **Navigate to the `utilScripts` directory**:
   ```bash
   cd <nameofyourownfile>/utilScripts
   ```
2. **Run the initialization script**:
   ```bash
   ./<initialize-script-name>
   ```

## Step 4: Start the Application

1. **Ensure you are still in the `utilScripts` directory**:
   ```bash
   cd <nameofyourownfile>/utilScripts
   ```
2. **Run the script to start the application, providing a name for your website**:
   ```bash
   ./startapp(the name might be different is around the range of stepAPP) <your-name>


   ## Step 5: Modify the Application Files

1. **Open the newly created application directory** (named in Step 4) in **VS Code**:
   ```bash
   code <your-file-name>
   ```
2. **Modify the `models.py` file** inside your application directory:
   - Define your data models.

3. **Create a CSS file** inside the `static/css/` directory:
    ## in the vs code folder your open is under static and css
   - Add custom styles for your application.

4.  **Create an HTML file** inside the template directory:
  ## in the vs code folder your create template under your file
   - Add your basic HTML structure.

## Step 6: Register the Application in Settings

1. **you have a `base.py` uder the settings file under the YourWebsiteNameMain, also add the application name there**:
## you can just do it in vs code
   - Add the name in the `INSTALLED_APPS` entry.


## Step 7: Run Migrations and Start the Server

1. **Navigate to the `utilScripts` directory**:
   ```bash
   cd <nameofyourownfile>/utilScripts
   ```
2. **Run migrations using the script**:
   ```bash
   ./makemigration
   ```
3. **Start the server**:
   ```bash
   ./runserver
   ```

Now, your application is fully registered, migrated, and running on the server.
