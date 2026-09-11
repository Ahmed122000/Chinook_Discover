# Chinook_Discover 🎵

A beginner-friendly project to practice **Python** and **SQL** using the Chinook music database.

## Overview

This project explores the Chinook database, a comprehensive music store dataset containing information about albums, artists, customers, invoices, and tracks. It demonstrates key SQL queries and Python data analysis techniques.

## 📊 Database Structure

The project uses the **Chinook SQLite database** with 11 tables:

| Table | Records | Purpose |
|-------|---------|---------|
| **Album** | 347 | Album information linked to artists |
| **Artist** | 275 | Artist details |
| **Customer** | 59 | Customer information and support representatives |
| **Employee** | 8 | Employee records with management hierarchy |
| **Genre** | 25 | Music genre classifications |
| **Invoice** | 412 | Invoice records with billing details |
| **InvoiceLine** | 2,240 | Individual line items from invoices |
| **MediaType** | 5 | Media format types |
| **Playlist** | 18 | Playlist collections |
| **PlaylistTrack** | 8,715 | Tracks assigned to playlists |
| **Track** | 3,503 | Individual tracks with pricing and metadata |

### Entity Relationships

```
Artist ← Album ← Track → Genre
                   ↓
            InvoiceLine → Invoice → Customer → Employee
                              ↑
                          Playlist
```

**Key Foreign Keys:**
- `Album.ArtistId` → `Artist.ArtistId`
- `Track.AlbumId` → `Album.AlbumId`
- `Track.GenreId` → `Genre.GenreId`
- `Track.MediaTypeId` → `MediaType.MediaTypeId`
- `Invoice.CustomerId` → `Customer.CustomerId`
- `Customer.SupportRepId` → `Employee.EmployeeId`
- `InvoiceLine.TrackId` → `Track.TrackId`
- `InvoiceLine.InvoiceId` → `Invoice.InvoiceId`
- `PlaylistTrack.PlaylistId` → `Playlist.PlaylistId`
- `PlaylistTrack.TrackId` → `Track.TrackId`

## 📁 Project Files

- **`Chinook_Discover.ipynb`** - Jupyter Notebook with exploratory data analysis and SQL queries
- **`Chinook_Sqlite.sqlite`** - SQLite database file containing all data
- **`LICENSE`** - MIT License
- **`.gitignore`** - Standard Python/Jupyter ignore rules

## 🚀 Getting Started

### Prerequisites

```bash
python 3.x
pandas
numpy
matplotlib
sqlite3 (built-in)
jupyter notebook
```

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Ahmed122000/Chinook_Discover.git
cd Chinook_Discover
```

2. Install dependencies:
```bash
pip install pandas numpy matplotlib jupyter
```

3. Start Jupyter Notebook:
```bash
jupyter notebook
```

4. Open `Chinook_Discover.ipynb` and run the cells

## 📝 Key Queries

### 1. Top 10 Best-Selling Tracks

Find the most profitable tracks by revenue:

```sql
SELECT t.Name as Name, Sum(il.Quantity) AS quantity, SUM(il.Quantity * il.UnitPrice) AS Total_Revenue
FROM InvoiceLine as il JOIN Track as t
ON il.TrackId = t.TrackId
GROUP BY t.TrackId, t.name
ORDER BY Total_Revenue DESC, t.name
LIMIT 10;
```

**Results Overview:**
- Top performers include tracks like "Gay Witch Hunt", "Hot Girl", and "How to Stop an Exploding Man"
- Best-selling tracks generate $3.98-$1.99 in revenue per entry

### 2. Highest Revenue by Country

Identify which country generates the most revenue:

```sql
SELECT BillingCountry, ROUND(SUM(Total), 2) As Total_Revenue 
FROM Invoice 
GROUP BY BillingCountry
ORDER BY Total_Revenue DESC
LIMIT 1;
```

## 💡 Learning Objectives

This project demonstrates:

- ✅ **SQL Fundamentals**: SELECT, JOIN, GROUP BY, ORDER BY, aggregation functions
- ✅ **Database Exploration**: Exploring schema, tables, columns, and relationships
- ✅ **Python Data Analysis**: Using Pandas to manipulate and visualize data
- ✅ **Data Visualization**: Creating plots and charts with Matplotlib
- ✅ **Database Connectivity**: Connecting to SQLite with Python
- ✅ **Best Practices**: Proper query structure and data analysis workflows

## 📊 Analysis Highlights

The notebook includes:

1. **Database Exploration**
   - Table discovery and row counts
   - Schema inspection (columns, data types, constraints)
   - Foreign key relationships
   - Index information

2. **Data Queries**
   - Top-selling tracks analysis
   - Revenue by country analysis
   - Additional analytics queries

3. **Data Visualization**
   - Bar charts for track revenue
   - Performance comparisons

## 🎓 Perfect For

- Beginners learning SQL and Python
- Students practicing database concepts
- Anyone wanting to understand relational databases
- Learning data analysis workflows

## 📚 Resources

### Project Reference
- **Project Roadmap**: [Querying SQL Python - roadmap.sh](https://roadmap.sh/projects/querying-sql-python)

### Database Source
- **Chinook Database**: [lerocha/chinook-database](https://github.com/lerocha/chinook-database)
- **Database File**: [Chinook_Sqlite.sqlite](https://github.com/lerocha/chinook-database/blob/master/ChinookDatabase/DataSources/Chinook_Sqlite.sqlite)

### Documentation
- [SQLite Documentation](https://www.sqlite.org/docs.html)
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [SQL Tutorial](https://www.w3schools.com/sql/)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Feel free to fork this project, submit issues, and create pull requests for improvements!

## 👤 Author

**Ahmed122000**

---

**Happy Learning! 🎉**

*This project is a great starting point for understanding databases and data analysis. Explore the Chinook dataset and experiment with your own SQL queries!*
