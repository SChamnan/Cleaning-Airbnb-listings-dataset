# Clean Airbnb Dataset using Python
`listings` dataset is donwloaded from [Inside Airbnb](https://insideairbnb.com/get-the-data/). The purpose of data cleaning is to filter, patch, and curate data in order to make it ready for analysis use.

I will use Jupyter Notebook to host this cleaning work. For details of Python code used, please view python file which is also included in this repo.
Let's get start!

## Data Cleaning
First, the following packages are imported, which are used to analyze and clean data. 
- pandas
- numpy
- seaborn
- matplotlib.pyplot

Next, I load and read data, reviewing the high level of columns properties and observing any obvious missing values.
Moreover, a heatmap below presents 5 columns with missing values which are needed to be cleaned and patched. 

Column Names with missing values
- `neighbourhood_group` - 100% missing values
- `price` - 17% missing values
- `last_review` - 22% missing values
- `reviews_per_month` 22% missng values
- `license` - 34% missing values

![image](https://github.com/user-attachments/assets/cb080d9c-6ebb-48cd-9d4a-168c3b9d7216)
![image](https://github.com/user-attachments/assets/db6e1d9c-2186-48af-b3dc-0fd7d7e18e36)


### Handling Columns with Missing Values
1. Drop `neighbourhood_group` column - I decided to drop this column because it has no data at all.
![image](https://github.com/user-attachments/assets/f6fe17d3-ea2a-4e44-96ec-863ca770772c)

3. Replace missing values in `last_review` and `license` columns with 'NA'
![image](https://github.com/user-attachments/assets/5e5da7a5-032a-4003-b02d-eb873224bf72)

4. Replace missing values in `reviews_per_month` and `price` with average values - I replace missing values in reviews_per_month column with mean = 1.79. Similarly, I also replace missing values in price column with mean = 184.68.
![image](https://github.com/user-attachments/assets/7280b881-1c6d-44cb-ae25-5df7d15fd377)

Subsequently, the heatmap shows no presence of missing values.
![image](https://github.com/user-attachments/assets/45d1afb4-6958-454a-b678-7549010d345d)

### Handling Outliers
The next step is to detect any outliers and decide what to do with them. According to box plots shown below, there are outliers in `price`, `minimum_nights` columns. I decided to remove the extreme values outliers. Handling outliers during data cleaning process would greatly help when we do any further indepth analysis as they tend to cause issues later.

After removing extreme outliers in `price` column
![image](https://github.com/user-attachments/assets/12788cb6-69d7-4ee3-9e13-0daac1d7b434)

Before and after removing extreme outliers in `minimum_night` column
![image](https://github.com/user-attachments/assets/9df6a358-2357-4226-b4fc-31793f27ebbc)

### Handling Sensitive Data
In real world practice, all PII information are hashed to protect owners and users' identity. In listings dataset, `host_id` and `host_name` data are exposed as they are not properly hashed. We can attempt to hash these columns but since I don't plan to use them in my dashboard development, I decided to drop both columns.
![image](https://github.com/user-attachments/assets/7fcf684c-6de6-4f99-aa0a-7938991d9f80)

Finally, after cleaning and brushing up the dataset, we export the cleaned dataset from Jupyter Notebook for any further analysis.
