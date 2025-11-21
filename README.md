# WEB-scraping-and-APIs

🎯 Project Overview

The e-scooter-sharing startup Gans aspires to operate in the most populous cities all around the world. Scooter movements are strongly influenced by weather conditions and arrivals of people in close-by airports. 
The aim of the project was to collect weather data in order to help the startup predict the scooters' movements and flights' information.

We create therefore a pipeline that extracts data from 3 different sources, one will be web scrapping (to get latitude and longitude of the cities) and the other two (weather and flights infos) will be APIs. 

This data is transformed using Python and finally, the data will be stored in a SQL database.

🛠️ Technologies and method used

Programming:
- Python

Tools:
- web scraping
- APIs

Environment:
- Google Colab
- Jupyter Notebook

🚀 Main steps and strategies:

- Collect data about cities (latitude and longitude) by web scraping and create a DataFrame:
  Python code:
   for city in cities:
    url = f"https://www.wikipedia.org/wiki/{city}"
    headers = {'User-Agent': 'Chrome/134.0.0.0'}

    response = requests.get(url, headers=headers)
    city_soup = BeautifulSoup(response.content, 'html.parser')
    city_latitude = city_soup.find(class_="latitude").get_text()
    city_longitude = city_soup.find(class_="longitude").get_text()
    country = city_soup.find(class_="infobox-data").get_text()

   city_data.append({"city": city,
                    "country": country,
                    "latitude": parse(city_latitude), # latitude in decimal format
                    "longitude": parse(city_longitude), # longitude in decimal format
                    })
 cities_df = pd.DataFrame(city_data)

- 

