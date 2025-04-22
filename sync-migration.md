# How to Resync Migrations and Clean Your Wagtail/Django Project

## Menu

- [Step 1: Clone the Project Repository](#step-1-clone-the-project-repository)
- [Step 2: Copy the Database File (Optional)](#step-2-copy-the-database-file-optional)
- [Step 3: Set Up Environment and Install Dependencies](#step-3-set-up-environment-and-install-dependencies)
- [Step 4: Clean Old Migrations and Temporary Files](#step-4-clean-old-migrations-and-temporary-files)
- [Step 5: Make Migrations](#step-5-make-migrations)
- [Note: Why Clean Migration Files?](#note-why-clean-migration-files)

---

## Step 1: Clone the Project Repository

```bash
mkdir tmp
cd tmp
git clone git@github.com:AEJJ-Studio-2025/laiyff-web-dev.git
cd laiyff-web-dev
```

### Explanation:
- `mkdir tmp`: Creates a temporary directory to contain your clone.
- `cd tmp`: Moves into that directory.
- `git clone ...`: Clones the remote repository using SSH.
- `cd laiyff-web-dev`: Enters the newly cloned project directory.

---

## Step 2: Copy the Database File (Optional)

If you have a saved database file you want to use:

```bash
cp /path/to/db.20250222 db.sqlite3
```

### Explanation:
- `cp /path/to/db.20250222 db.sqlite3`: Copies your saved database and renames it to `db.sqlite3` so Django can use it directly.

> 🔍 Tip: Make sure the file you copy is a valid SQLite database file. Adjust the path accordingly.

---

## Step 3: Set Up Environment and Install Dependencies

Run the environment setup script provided in `utilScripts`:

```bash
cd utilScripts
./initialEnv.sh
```

### Explanation:
- `cd utilScripts`: Navigates to the directory containing helper scripts.
- `./initialEnv.sh`: This script typically:
  - Creates a Python virtual environment.
  - Installs Python packages from `requirements.txt`.
  - Sets up `.env` or other necessary local configuration.

---

## Step 4: Clean Old Migrations and Temporary Files

Use `git clean` to delete any untracked or generated files:

```bash
git clean -d -f -x
```

### Explanation:
- `-d`: Includes directories.
- `-f`: Forces deletion (required for safety).
- `-x`: Removes all untracked files **including files ignored by `.gitignore`**.

This removes:
- Old migration files.
- Compiled Python files (`__pycache__`, `.pyc`).
- Any other local files that are not tracked by Git.

> ⚠️ **Warning**: This command is **irreversible**. Be sure to back up or stage any important changes using `git add`.

---

### Optional: Protect Files You Want to Keep

Before running `git clean`, protect files using:

```bash
git add your_app/migrations/__init__.py
```

This ensures essential files like the `__init__.py` in your `migrations` folder aren’t deleted.

---

## Step 5: Make Migrations

After cleaning your environment, regenerate fresh migration files:

```bash
./makeMigrations.sh
```

### Explanation:
- This script likely wraps the Django command:
  ```bash
  python manage.py makemigrations
  ```
- It scans your `models.py` files and creates new migration files under:
  ```
  your_app/migrations/
  ```

You should see output confirming which apps had migrations generated.

---

## Note: Why Clean Migration Files?

Cleaning and regenerating migrations may be necessary when:

- You've changed model structure and want a clean migration history.
- You're running into migration conflicts across branches or contributors.
- Your database schema is out of sync with your model definitions.
- You want to consolidate messy migration chains before production.

Cleaning ensures a **consistent, reliable, and reproducible** migration state across development environments.

---

After following all steps, you should have:
- A clean working directory.
- A valid database (if applicable).
- Fresh migrations in sync with your models.
- A working virtual environment with dependencies installed.
