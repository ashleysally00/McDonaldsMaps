# McDonald's Data Project: Heat Map, Bar Graph, Drive-Through Analysis, and Machine Learning Modeling

[see the maps here](https://66d78831d6f7dfd6e93d89aa--coruscating-cobbler-7c06de.netlify.app/)

## 1. Dataset Acquisition and Setup
I downloaded [this free list of all McDonald's locations-related data in the United States](https://data-m8.com/products/list-of-all-mcdonalds-locations-in-the-us-csv-and-json), which is no longer free (I don't know why).

I imported the CSV into Visual Studio Code (VSC) in a Jupyter notebook for analysis. The dataset includes various columns such as `store_brand`, `store_id`, `city`, `state_code`, `open_hours_drive_through`, etc.

## 2. Data Filtering and Preparation

### Filtering for California
I used Data Filtering with pandas to select rows where the `state_code` or `state_name` matched "CA" or "California". This was achieved using pandas DataFrame operations (e.g., `df[df['state_code'] == 'CA']`).

### Identifying Drive-Through Locations
I used boolean indexing to filter the dataset to include only locations with drive-through information by checking the `open_hours_drive_through` column. I applied a boolean mask to select rows where this column indicated the presence of a drive-through. You create a boolean mask to ask if a condition, like whether a drive-through exists, is true or false. Boolean indexing is where you check that condition across your dataset. 

### Filtering for Specific Hours
I further filtered the data to identify drive-throughs open at 3 AM by using Conditional Statements. I checked if the `open_hours_drive_through` column contained information indicating that the drive-through was open at 3 AM (e.g., `df[df['open_hours_drive_through'].str.contains('03:00')]`).

## 3. Creating the Heat Map
I used Folium to create a heat map to visualize the density of McDonald's locations in California.  
I also applied Geospatial Techniques to generate the heat map. This involved converting the filtered data into latitude and longitude coordinates and using Folium’s HeatMap function to display areas with higher concentrations of McDonald's locations. It meant using Leaflet for JavaScript under the hood so I could display my interactive map directly in my web application. Folium is a libray that is good for converting interactive maps you are making with Python into HTML so you can display them on your webpages. 

## 4. Creating the Bar Graph
I created a bar graph to visualize the distribution of McDonald's locations across different regions or states.  
I used Pandas and Matplotlib for this task. I aggregated the number of McDonald's locations by region or state using pandas’ grouping and aggregation functions, then plotted this data using Matplotlib’s bar plot functions.

## 5. Machine Learning Analysis

### Machine Learning Modeling
I imported libraries from scikit-learn for model training and evaluation. In preparing the data, I used latitude and longitude as the features (X) for the model. Then I created a binary target variable `drive_through` based on whether drive-through hours were present (1 if present, 0 if not). I then split the dataset into training and testing sets using the `train_test_split` function.

I initialized the Random Forest classifier with 100 trees (`n_estimators=100`) because it is a common number people have used for testing, and a fixed random state to ensure consistent results. Then, I trained the model using the training data (`X_train` and `y_train`) with the `fit` method. This step involved the model learning the patterns in the data. I used the trained model to predict the target variable for the testing set (`X_test`) and evaluated its performance using accuracy and classification metrics. I tested it to see if a drive-through would be present. It was.

## 6. HTML Integration
I added the generated map, heat map, and bar graph to an `index.html` file.  
I ensured that the titles of the maps and graphs were properly aligned above the corresponding visualizations to maintain a clean layout.

## 7. Deployment
I deployed the HTML file displaying the map on a webpage through Netlify, making the interactive map accessible online. This webpage focused on McDonald's locations.
