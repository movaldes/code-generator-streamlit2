This Python script scrapes information about public restrooms in Miami, FL, from a Yelp search results page. Using the requests library, it retrieves the HTML content of the specified URL. The HTML is then parsed with BeautifulSoup to locate specific elements on the page containing details like the restroom's name, rating, review count, address, and phone number, which are identified by their respective HTML tags and classes.

The extracted information is stored in a dictionary, where each restroom's name serves as the key, and its details (e.g., rating, reviews, address, and phone) are organized as values. The script then converts this dictionary into a Pandas DataFrame for easy viewing and further analysis, printing the data in a tabular format.

However, the script assumes a specific structure of Yelp's HTML, which may change over time. Additionally, as Yelp dynamically renders much of its content using JavaScript, this approach might not work without a tool like Selenium to handle JavaScript execution. The script also lacks error handling, which may lead to failures if any expected data is missing.
