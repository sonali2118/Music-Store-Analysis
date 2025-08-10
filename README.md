# 🎵 Music Store Analysis Using SQL

## 📌 Project Overview
This project focuses on analyzing a fictional music store database using **SQL** queries.  
The goal is to extract meaningful insights about **sales performance, customer behavior, popular genres, and top-performing artists**.  

By running analytical queries on the dataset, we can help the store improve its marketing strategies and boost revenue.

---

## 📂 Dataset Description
The database contains the following main tables:

| Table Name   | Description |
|--------------|-------------|
| `albums`     | Album details including `AlbumId`, `Title`, `ArtistId`. |
| `artists`    | Artist information with `ArtistId` and `Name`. |
| `customers`  | Customer details including location and contact info. |
| `employees`  | Employee details for the store. |
| `genres`     | Genre information (`GenreId`, `Name`). |
| `invoices`   | Purchase records including date, customer, and total amount. |
| `invoice_items` | Details of each track purchased in an invoice. |
| `tracks`     | Track details including genre, album, composer, and price. |
| `media_types` | Type of media (MPEG, AAC, etc.). |
| `playlists` & `playlist_track` | Playlist details and associated tracks. |

---

## 🎯 Objectives
- Identify the **most popular music genres**.
- Find the **top-selling artists and albums**.
- Analyze **customer locations** to find the most profitable regions.
- Track **monthly and yearly sales trends**.
- Discover **top customers** by total spending.

---

## 🛠️ Tools & Technologies
- **SQL**: For querying and analysis.
- **Database**: MySQL 
  

---

## 📊 Example Queries
### 1️⃣ Top 5 Best-Selling Genres
```sql
SELECT g.Name AS Genre, COUNT(ii.Quantity) AS Total_Sales
FROM invoice_items ii
JOIN tracks t ON ii.TrackId = t.TrackId
JOIN genres g ON t.GenreId = g.GenreId
GROUP BY g.Name
ORDER BY Total_Sales DESC
LIMIT 5;
