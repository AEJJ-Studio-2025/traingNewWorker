How to Resync Migrations and Clean Your Wagtail/Django Project

This guide outlines the steps to resync migrations, reset the database, and start fresh in your Wagtail/Django project.

---

## Step 1: Clone the Project Repository

```bash
mkdir tmp
cd tmp
git clone git@github.com:AEJJ-Studio-2025/laiyff-web-dev.git
cd laiyff-web-dev
```

---

## Step 2: Copy the Database File (Optional)

If you have a database snapshot:

```bash
cp /path/to/db.20250222 db.sqlite3
```

---

## Step 3: Set Up Environment and Install Dependencies

Run the initial environment setup script:

```bash
cd utilScripts
./initialEnv.sh
./makeMigration.sh
```

This will install all required Python packages from `requirements.txt`.

---

## Step 4: Clean Old Migrations and Temporary Files

To start fresh and remove untracked files (including migrations and compiled Python files), run:

```bash
git clean -d -f -x
```

This command will remove:
- Compiled Python files (`__pycache__`)
- Old migration files
- Any other untracked or temporary files

> ⚠️ **Warning:** `git clean -d -f -x` is **destructive**. Make sure to commit or `git add` any files you want to keep. Tracked files will **not** be removed.

### You can use `git add` to protect files from being deleted:

```bash
git add base/< your file >

This ensures that your file won’t be removed by `git clean`.

---

## Note: Why Clean Migration Files?

Cleaning and regenerating migrations may be necessary when:
- You've made major changes to your models and migrations are out of sync.
- You're experiencing migration conflicts across branches or contributors.
- The database schema doesn't match your model definitions.
- You want to reset and consolidate migrations after prototyping.

Cleaning helps ensure a consistent and reproducible migration state, especially during early-stage development.

---

## Step 5: Make Migrations

After cleaning, regenerate the migration files:

```bash
./makeMigrations.sh
```

You should see new migration files created under each app’s `migrations/` folder.

---