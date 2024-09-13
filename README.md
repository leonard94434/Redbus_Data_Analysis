                                                  RedBus Web Scraping and Analysis 
Overview:

This project is designed to automate the process of scraping bus routes, details, and availability from the RedBus website. Using Selenium for web scraping and storing the gathered data in a MySQL database, this tool is perfect for anyone needing to gather real-time bus information for analysis or personal use.

The key features of the script include:

Dynamic web scraping using Selenium.
Handling multi-page scraping via user input.
Extracting important details like bus names, types, departure and arrival times, ratings, prices, and seat availability.
Storing data in a structured MySQL database for future reference and analysis.

Features:

Web Scraping with Selenium: Scrapes bus details including bus names, types, departure and arrival times, prices, and seat availability.
Data Storage in MySQL: The extracted data is stored in a MySQL database, allowing for easy retrieval and further processing.
Multi-page Scraping: The tool is designed to handle multiple pages of bus routes, with the user manually confirming pagination to ensure all data is captured.
Error Handling: Handles common web scraping errors such as missing elements, unclickable elements, and varying page structures.

Installation:

Python 3.x
WebDriver for Chrome or another browser (Ensure the path to the driver is set up correctly)
MySQL Server

Required Python Libraries:

You can install the required Python libraries using pip:

#pip install selenium

#pip install pymysql

Setting up MySQL:

Create a MySQL database called redbus_data1 (or modify the code to use your desired database name). Make sure your MySQL user has the necessary privileges to create tables and insert data.

How It Works:

1. Initializing WebDriver
The script starts by initializing Selenium WebDriver and navigating to the RedBus website. It clicks through the "View All" button under the Government Bus Corporations section, which takes the user to a new page where the bus routes are displayed.

2. Scraping Routes
The tool scrapes each available route by gathering the name and link. For each page, the user must confirm by clicking on the next page number and pressing Enter to continue.

3. Extracting Bus Details
For each route, the script navigates to the corresponding page and extracts the following details:

Bus Name
Bus Type
Departure Time
Arrival Time
Travel Duration
Star Rating
Ticket Price
Seat Availability

4. Data Storage
All the scraped data is stored in a MySQL database table bus_routes, with a schema that includes:

route_name
route_link
busname
bustype
departing_time
duration
reaching_time
star_rating
price
seats_available

5. Saving Data to MySQL
Once the data is scraped, the script connects to the MySQL database and inserts the data into the bus_routes table. The table is automatically created if it doesn't already exist.

6. Closing WebDriver
After completing the scraping and data insertion, the script safely closes the WebDriver instance.

Running the Script:

Run the script after installing all dependencies and setting up MySQL.
Make sure your WebDriver (e.g., ChromeDriver) is installed and configured.
Follow the instructions in the console to click through pages manually when required.

#python redbus_scraper.py 

Database Schema
SQL

CREATE TABLE IF NOT EXISTS bus_routes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    route_name TEXT,
    route_link TEXT,
    busname TEXT,
    bustype TEXT,
    departing_time DATETIME,
    duration TEXT,
    reaching_time DATETIME,
    star_rating FLOAT,
    price DECIMAL(10, 2),
    seats_available INT
);
Customization
Bus Corporation Selection: You can change the XPath in the code to target a different bus corporation.
Database: Modify the database connection parameters (host, user, passwd, db) to fit your local setup.
Known Limitations
Pagination: The user has to manually confirm when navigating through multiple pages.
Browser-Specific: The script is currently configured to use Chrome. If you prefer another browser, update the WebDriver setup accordingly.
Future Improvements
Automating pagination to remove the need for manual input.
Enhancing error handling for more robust scraping.
Adding multi-threading for faster data extraction.


License
This project is open-source and available for anyone to use and modify.

