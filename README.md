Tutorial: Installing PostGIS and Creating a Spatially-Enabled Database
1. Overview
   This guide provides detailed instructions for:

Installing PostgreSQL (the database management system),
Installing PostGIS (the spatial extension for PostgreSQL),
Creating a new database in pgAdmin,
Enabling PostGIS features within that database,
Verifying that PostGIS is operational.
Following these steps will help you set up a powerful platform for managing and querying spatial (GIS) data.

2. Install PostgreSQL
   Download the Installer

Go to the official PostgreSQL download page and locate the appropriate version for your operating system (Windows, Linux, or macOS).
Run the Installer

Launch the installer and proceed through the setup wizard.
When prompted, choose a convenient installation directory (or accept the default).
Set a password for the postgres superuser account. Keep it safe and easy to recall.
Use the OS-Specific Instructions (If Needed)

For detailed installation steps on your operating system, refer to the respective guides:
Windows Installation Guide
Linux Installation Guide
macOS Installation Guide
Note: Make sure you include all necessary components during installation (including Stack Builder, which you will need later to add PostGIS).

3. Install PostGIS
   Open Stack Builder

After completing the PostgreSQL installation, launch the Stack Builder tool. This tool helps you download and install additional components for PostgreSQL.
Select the PostgreSQL Version

In Stack Builder, choose the version of PostgreSQL you just installed.
Choose PostGIS

From the list of available add-ons, find PostGIS and select it. PostGIS adds powerful spatial capabilities to PostgreSQL.
Skip Creating a Spatial Database (Optional)

During the PostGIS setup, you may be asked whether you want to create a spatial database. You can skip this step since you will create and configure your database manually.
Finish the Installation

Complete the Stack Builder process to finalize the PostGIS installation.
4. Create a Database in pgAdmin
   Open pgAdmin

Locate and launch pgAdmin 4, which was installed alongside PostgreSQL.
Log In

Use the postgres superuser password you selected during the PostgreSQL installation.
Create a New Database

In the navigation pane on the left:
Expand Servers to see your PostgreSQL server.
Right-click on the server name and select Create > Database.
Provide a name for your database (for example, spatial_db_1).
Click Save to finalize.
5. Enable the PostGIS Extension
   Open the Query Tool

In pgAdmin, expand Databases, and then click your newly created database (e.g., spatial_db_1).
Right-click the database name and select Query Tool.
Run the CREATE EXTENSION Command

Type or paste the SQL command below into the Query Tool:
sql
Copier le code
CREATE EXTENSION postgis;
Execute the query (click the “play” button or press F5).
6. Verify the PostGIS Installation
   Check for Spatial Tables
   Within pgAdmin, expand:
   Databases > YourDatabase > Schemas > public > Tables.
   Locate the spatial_ref_sys Table
   Look for a table called spatial_ref_sys. If you see this table, it confirms that PostGIS has been successfully installed and is active on your database.
