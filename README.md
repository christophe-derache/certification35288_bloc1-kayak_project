# Bloc_1
### *Construction et alimentation d'une infrastructure de gestion de données*
## **Kayak**

- **Contact**: *Christophe DERACHE*
- **E-mail**&nbsp;&nbsp;: *christophe.derache@gmail.com*

> Video link : 👉 ************************************************ 👈

## Subject

>*The marketing team needs help on a new project. After doing some user research, the team discovered that 70% of their users who are planning a trip would like to have more information*
>*about the destination they are going to. In addition, user research shows that people tend to be defiant about the information they are reading if they don't know the brand which produced the content.*
>*Therefore, Kayak Marketing Team would like to create an application that will recommend where people should plan their next holidays. The application should be based on real data about:*
>
>    Weather
>    Hotels in the area
>
>*The application should then be able to recommend the best destinations and hotels based on the above variables at any given time.*

## How is my code organized? As follow, you'll find some relevant explanations about these several folders: 

- 1 - Get GPS Coordinates

The project start with a 35 cities list. Therefore, my firts goal was to obtain GPS coordinates about these 35 french cities.
For that, I've requested the Nominatim (openstreetmap) API.
Notebook = get_coordinates_from_list.ipynb
output = dict_gps.json


- 2 - Get Weather 35 destinations

Then, I've requested the Open Meteo API (open source meteo project), to realize a Dataframe containing 7 days predictions temperature, precipitations and weather code.

Notebook1 = get_weather_from_list.ipynb
output = weather_to_sort.csv

Notebook2 = sort_best_destinations.ipynb
output = weather_ready_to_sort.csv (merged with the hotels dataframe later on)
output = best_destinations_dataframe.csv (not reused during the following steps)


- 3 - Get Hotels 35 destinations

This step is the scrapping exercise. My code scrap data about 25 hotels for each 35 french destination list.

Notebook1 = scrap_booking.ipynb
output = 1 csv file per destination in "save_output" folder

Notebook2 = clean_and_concat_35_df.ipynb
output = df_hotels.csv in "cleaned_and_concat_hotels" folder


- 4 Merge store data S3 and RDS

First, I store data about weather and hotels separatively on my S3 Bucket. 

Then, I realize the Extract Transform Load process as follow:
- I verify my S3 public link downloading the 2 previous files and I merge them 
before storing the final result in the same S3 Bucket.
- Finally, after connecting my computer to my RDS Database, I send the whole data to my RDS Database.

Notebook1 = Merge_store_data_S3_and_RDS.ipynb
output = merged_weather_hotels_data.csv

Notebook2 = store_data_RDS.ipynb


- 5 - Vizualise through maps

Two maps were asked in this project, thus, I've realized 2 plots:
- 1 representing the 5 best destinations
- 2 representing the 25 hotels position regarding each best 5 destinations


- 6 - Screenshots

In this folder, you'll find all relevant screenshots realized during this project.
Especially those regarding the steps on "Amazon Web Service" cloud technologies.



