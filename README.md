
<p align="center">
<img width="1000" height="400" alt="TempVLat" src=https://media.giphy.com/media/nJ2PObJA3EVgc/giphy.gif?cid=ecf05e47ytjaauo8d4zzzb127sbgfho5y0vbozdbfxafp3qq&ep=v1_gifs_search&rid=giphy.gif&ct=g>

***

<h1 align="center">Eat Safe, Love</h1>

The NoSQL_setup.ipynb file is responsible for configuring and maintaining the database, while the NoSQL_analysis.ipynb file retrieves pertinent data for analysis and transforms the outcomes into Pandas DataFrames. The data from the establishments.json file was imported via the Terminal using the command mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json.

<h1 align="center">Set Up and Update Database</h1>

* Insert the new halal restaurant opened in Greenwich to the Database.
    ```
    establishments.insert_one(new_restaurant)
    ```
    
* Update the new restauarant with the correct BusineesTypeID.
    ```
    establishments.update_one(new_restaurant,{'$set':{'BusinessTypeID':1}})
    ```
    
* Drop all establishments that has Dover as their Local Authority from the database. 
    ```
    establishments.delete_many({'LocalAuthorityName':'Dover'})
    ```
    
* Convert latitude and longitude to decimal numbers.
    ```
    establishments.update_many({},{'$set':{'geocode.longitude':{'$toDouble':'$geocode.longitude'}
    ,'geocode.latitude':{'$toDouble':'$geocode.latitude'}}}])

    ```
    
<h1 align="center">Exploratory Analysis</h1>

1. Which establishments have a hygiene score equal to 20?
   
   There are 41 establishments with a hygiene score of 20.
   
2. Which establishments in London have a RatingValue greater than or equal to 4?

    There are 33 establishments in London that have a RatingValue greater than or equal to 4.

3. What are the top 5 establishments with a RatingValue rating value of '5', sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

   The top 5 establishments with a RatingValue of '5' sorted by lowest hygiene score nearest to "Penang Flavours" are: "Greenwich", "Lumbini Grocery Ltd T/A Al-Iman", "Atlantic Fish Bar", "Iceland", and "Volunteer". 
   
4. How many establishments in each Local Authority area have a hygiene score of 0?
    ```   
    There are 55 rows in the DataFrame.
   
        _id             count
    0    Thanet             1130
    1    Greenwich          882
    2    Maidstone          713
    3    Newham             711
    4    Swale              686
    5    Chelmsford         680
    6    Medway             672
    7    Bexley             607
    8    Southend-On-Sea    586
    9    Tendring           542

    ```

<h1 align="center">References</h1>

SOFTWARE/TOOLS/LIBRARIES


<img width="120" height="80" alt="PyMongo" src=https://github.com/alejandro-davila/NoSQL/assets/135288005/2fe8ba54-d55d-4883-9743-5b14715497bb>
<img width="90" height="90" alt="Jupyter" src=https://github.com/alejandro-davila/NoSQL/assets/135288005/b676969a-d5c4-405b-abea-c1ad27986df4>
<img width="90" height="70" alt="Jupyter" src=https://github.com/alejandro-davila/NoSQL/assets/135288005/cf788bf2-1b9d-484e-89d2-2367ff9c28a1>
<img width="90" height="70" alt="Jupyter" src=https://github.com/alejandro-davila/NoSQL/assets/135288005/ef6d1bde-f15c-4cec-932c-ee4a31cebf23>


