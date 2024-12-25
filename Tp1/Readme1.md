Thought about PostGIS installation guide pendant quelques secondes

# 🗺️ TD-1: Installing PostGIS and Creating a Spatially-Enabled Database

## 📖 Overview

Follow this tutorial to set up PostgreSQL, install the PostGIS extension, create a spatial database, and confirm your configuration is correct. By the end, you’ll be ready to manage and analyze spatial data.

---

## 🚀 Step 1: Install PostgreSQL

1. **Download PostgreSQL**
   
   - Visit the [official PostgreSQL website](https://www.postgresql.org/download/) and choose the appropriate version for your operating system (Windows, Linux, or macOS).

2. **Run the Installation**
   
   - Follow the instructions in the setup wizard.
   - Choose a secure yet memorable password for the `postgres` user.

3. **Refer to OS-Specific Guides (Optional)**
   
   - [Windows Installation Guide](https://www.postgresql.org/download/windows/)
   - [Linux Installation Guide](https://www.postgresql.org/download/linux/)
   - [macOS Installation Guide](https://www.postgresql.org/download/macosx/)

---

## 🚀 Step 2: Install PostGIS

1. **Include Stack Builder**
   
   - During the PostgreSQL installation, make sure to include **Stack Builder**.

2. **Launch Stack Builder**
   
   - After installing PostgreSQL, open **Stack Builder**.

3. **Select Your PostgreSQL Version**
   
   - In Stack Builder, pick the version of PostgreSQL you just installed.

4. **Install PostGIS**
   
   - Locate **PostGIS** in the list of available extensions and select it.
   - (Optional) Skip the prompt to create a spatial database, as you’ll create it manually.

5. **Complete the Installation**
   
   - Follow the remaining steps to finish installing PostGIS.

---

## 🚀 Step 3: Create a Database in pgAdmin

1. **Open pgAdmin 4**
   
   - This tool is installed alongside PostgreSQL.

2. **Log In**
   
   - Sign in using the `postgres` user’s password from the installation.

3. **Create a New Database**
   
   - In pgAdmin:
     - Expand **Servers**, then right-click your PostgreSQL server.
     - Select **Create** > **Database**.
   - Enter a database name (e.g., `spatial_db_1`) and click **Save**.

---

## 🚀 Step 4: Enable the PostGIS Extension

1. **Open the Query Tool**
   
   - In pgAdmin, expand **Databases** and select your new database (e.g., `spatial_db_1`).
   - Right-click the database name and choose **Query Tool**.

2. **Run the SQL Command**
   
   sql
   
   Copier le code
   
   `CREATE EXTENSION postgis;`

---

## 🚀 Step 5: Verify the PostGIS Installation

1. **Check the Tables**
   
   - In pgAdmin, open:
     - **Databases** > **YourDatabase** > **Schemas** > **Public** > **Tables**.

2. **Find `spatial_ref_sys`**
   
   - If you see the table named **spatial_ref_sys**, PostGIS has been successfully enabled in your database.
