# 🌍 TD-2: Creating Spatial Tables in PostgreSQL

This tutorial shows you how to create spatial tables in PostgreSQL with PostGIS, add data through QGIS, and validate your data with SQL queries.

---

## 🗂️ Table of Contents

1. Creating a Spatial Table (Points)
2. Creating a Spatial Table (Polygons)
3. Creating a Spatial Table (LineStrings)
4. Using QGIS to Insert Data

---

## 🚀 Step 1: Creating a Spatial Table (Points)

### 📋 SQL Command

Use the following SQL script in pgAdmin to create a table named **points_of_interests** with a Point-type geometry column:

sql

Copier le code

`CREATE TABLE points_of_interests (   id SERIAL PRIMARY KEY,   nom VARCHAR(255),   geom GEOMETRY(Point, 4326) );`

### 🛠️ Using QGIS to Insert Data

1. **Open QGIS** and set up a connection to your database:
   - In the **Explorer** panel, right-click on **PostgreSQL**.
   - Choose **New Connection** and enter your database details. Test the connection to confirm.
2. **Add the `points_of_interests` table** as a layer:
   - Double-click on the table to load it into QGIS.
3. **Switch to Edit Mode**:
   - Place points on the map where desired.
   - Save your edits to store them in the database.

### 🔍 Verifying Data

In **pgAdmin**, run:

sql

Copier le code

`SELECT *  FROM points_of_interests;`

Confirm that your newly added records are listed.

---

## 🚀 Step 2: Creating a Spatial Table (Polygons)

### 📋 SQL Command

In pgAdmin, create a **zones_protegees** table with a Polygon geometry column:

sql

Copier le code

`CREATE TABLE zones_protegees (   id SERIAL PRIMARY KEY,   nom VARCHAR(255),   geom GEOMETRY(Polygon, 4326) );`

### 🛠️ Using QGIS to Insert Data

1. **Load the `zones_protegees` table** in QGIS, following the same steps as in **Step 1**.
2. **Switch to Edit Mode**:
   - Draw polygons on the map.
   - Save your changes to update the database.

### 🔍 Verifying Data

In **pgAdmin**, run:

sql

Copier le code

`SELECT * FROM zones_protegees;`

Check that your polygons appear in the result set.

---

## 🚀 Step 3: Creating a Spatial Table (LineStrings)

### 📋 SQL Command

Use this command in pgAdmin to create a **routes** table with a LineString geometry column:

sql

Copier le code

`CREATE TABLE routes (   id SERIAL PRIMARY KEY,   nom VARCHAR(255),   geom GEOMETRY(LINESTRING, 4326) );`

### 🛠️ Using QGIS to Insert Data

1. **Load the `routes` table** in QGIS.
2. **Activate Edit Mode**:
   - Draw lines on the map.
   - Save your work to commit the changes.

### 🔍 Verifying Data

In **pgAdmin**, run:

sql

Copier le code

`SELECT * FROM routes;`

Ensure that your newly drawn routes are shown in the query results.

---

## 🛠️ Using QGIS to Insert Data (General Tips)

Regardless of which geometry type you’re working with:

1. **Connect** to your PostgreSQL database in QGIS.
2. **Load** the table as a layer.
3. **Enable Edit Mode** to add or modify your points, polygons, or lines.
4. **Save** your edits to write them back to the database.

---

## 🏁 Summary

By following these steps, you’ve:

- Created three spatial tables (`points_of_interests`, `zones_protegees`, and `routes`) for storing points, polygons, and lines.
- Populated each table with data using QGIS.
- Verified the contents of each table via SQL queries in pgAdmin.
