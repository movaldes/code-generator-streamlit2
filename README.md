```
import requests
from bs4 import BeautifulSoup
import pandas as pd

# URL of the website to be scraped
url = "https://www.yelp.com/search?find_desc=public+restrooms&find_loc=Miami%2C+FL"

# Send a request to the website and get the HTML response
response = requests.get(url)

# Parse the HTML content using Beautiful Soup
soup = BeautifulSoup(response.content, "html.parser")

# Find the list of public restrooms on the website
restrooms = soup.find_all("div", {"class": "public-restroom"})

# Create a dictionary to store the information of each restroom
restroom_info = {}

# Loop through each restroom and extract the necessary information
for restroom in restrooms:
    # Get the name of the restroom
    name = restroom.find("h3", {"class": "name"}).text.strip()

    # Get the rating of the restroom
    rating = restroom.find("span", {"class": "rating"}).text.strip()

    # Get the number of reviews of the restroom
    reviews = restroom.find("span", {"class": "review-count"}).text.strip()

    # Get the address of the restroom
    address = restroom.find("span", {"class": "address"}).text.strip()

    # Get the phone number of the restroom
    phone = restroom.find("span", {"class": "phone"}).text.strip()

    # Add the information to the dictionary
    restroom_info[name] = {
        "rating": rating,
        "reviews": reviews,
        "address": address,
        "phone": phone
    }

# Create a Pandas DataFrame from the dictionary
df = pd.DataFrame.from_dict(restroom_info, orient="index")

# Print the DataFrame
print(df)
```
This code will send a request to the Yelp website and extract the information of the public restrooms in Miami, Florida. It will then create a Pandas DataFrame from the extracted information and print it.

Note: This code assumes that the Yelp website has the same HTML structure as when the code was written. If the website has changed, the code may not work as expected.
