# 🌍 TD-3: SQL Spatial Functions in PostGIS

This exercise focuses on using PostGIS spatial functions to determine how many parcels fall within a 1 km radius of designated fire points. You’ll learn how to import a shapefile into PostGIS, perform spatial queries, and visualize your results in QGIS.

---

## 🗂️ Table of Contents

1. [Import the Shapefile into PostGIS](#import-the-shapefile-into-postgis)
2. [Queries to Analyze the Data](#queries-to-analyze-the-data)
   - [Count Total Number of Parcels](#count-total-number-of-parcels)
   - [Get Fire Point (Centroid of Parcel 462273)](#get-fire-point-centroid-of-parcel-462273)
   - [Parcels within a 1 km Radius of Fire Point](#parcels-within-a-1-km-radius-of-fire-point)
   - [Filter for Two Zones](#filter-for-two-zones)
3. [Advanced Spatial Queries](#advanced-spatial-queries)
   - [Count Parcels within 1 km of Both Zones](#count-parcels-within-1-km-of-both-zones)
   - [Calculate Total Area of Parcels near Fire Points](#calculate-total-area-of-parcels-near-fire-points)
4. [Additional Resources](#additional-resources)

---

## 1. Import the Shapefile into PostGIS

### 🛠️ Steps

1. **Download the Shapefile**
   - Make sure you have the Florida parcels shapefile saved locally.
2. **Open the PostGIS Shapefile Import/Export Manager**
   - On Windows, press the **Windows key** and search for **Shapefile Import/Export Manager**.
3. **Select the Shapefile to Import**
   - Browse to the **Florida parcels** shapefile.
   - Choose a target schema and table name in your PostgreSQL database.
4. **Begin Import**
   - Click **Import** to load the data into PostgreSQL.

Your parcels data should now be stored in a database table (often named `parcels`).

---

## 2. Queries to Analyze the Data

### 2.1 Count Total Number of Parcels

Use this query to get an overall count of rows in the `parcels` table:

sql

Copier le code

`SELECT COUNT(*)  FROM parcels;`

**Result**: The total number of parcel records in your database.

---

### 2.2 Get Fire Point (Centroid of Parcel 462273)

Find the geographic center of parcel with `gid = 462273`:

sql

Copier le code

`SELECT ST_Centroid(geom) AS fire_point FROM parcels WHERE gid = 462273;`

**Result**: A single **Point** geometry (the centroid) of that specific parcel.

---

### 2.3 Parcels within a 1 km Radius of Fire Point

In **QGIS**, you can filter parcels that are within 1 km of the fire point from parcel 462273. The spatial function `ST_DWithin` checks if the distance between two geometries is less than or equal to a given threshold (in meters, by default).

**QGIS Filter Expression**:

sql

Copier le code

`ST_DWithin(   geom,   (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273),   1000 )`

**Result**: Displays only parcels located within 1 km of the centroid of parcel 462273 in QGIS.

---

### 2.4 Modify the Filter for Two Zones

To filter parcels within 1 km of **either** parcel 462273 or 460957, extend the query:

sql

Copier le code

`ST_DWithin(   geom,   (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273),    1000 ) OR  ST_DWithin(   geom,   (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957),   1000 )`

**Result**: Only parcels that are within 1 km of **either** parcel’s centroid will be displayed.

---

## 3. Advanced Spatial Queries

### 3.1 Count Parcels within 1 km of Both Zones

You can run this query in **pgAdmin** or **psql** to see how many parcels lie within 1 km of **either** centroid:

sql

Copier le code

`SELECT COUNT(*)  FROM parcels  WHERE ST_DWithin(   geom,    (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273),    1000 ) OR ST_DWithin(   geom,    (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957),   1000 );`

**Result**: Returns a numerical count of parcels that fall in the 1 km radius of **at least one** of the two fire points.

---

### 3.2 Calculate Total Area of Parcels near Fire Points

To find the cumulative area of these parcels, use:

sql

Copier le code

`SELECT SUM(ST_Area(geom))  FROM parcels  WHERE ST_DWithin(   geom,    (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273),    1000 ) OR ST_DWithin(   geom,    (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957),    1000 );`

**Result**: Provides the **total area** of all parcels located within 1 km of the selected fire points.

---

## 4. Additional Resources

- **PostGIS Documentation**
- **QGIS Documentation**
