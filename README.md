# Linearity
---

## Files & Directories
---

- Data directory containing csv's of the 2 datasets
- Task description PDF
- Jupyter Analysis Notebook
- Metabase Dashboard PDF

## How I approached this task
---
1. Created a Jupyter Notebook to execute Python to access postgres / s3 data
2. Completed all questions from section 3 in Notebook on a flight, given the possibility of working without an internet connection
    - Jupyter Notebook should not to be considered as a polished analysis
    - Answers should be correct, but the goal was to familiarise myself with the data / solutions, before completing task in BI Solution
    - Jupyter Notebook can nonetheless provide some indication of my comfort within the tool
3. BI Solution
    - Created Metabase Instance, with 14-day Trial
    - Uploaded CSV's into Sample Database and answered all questions, before running into Dashboard performance issues
    - Resumed a paused Redshift database on EC2 cluster
    - Created 2 new tables and imported the data
    - Connected Redshift database to Metabase and adjusted underlying queries / questions

## Solutions
---
### 1: Python Code  to access postgres database & copy the user data in a Google sheet/csv.
```python
# Database connection params
host='linearity-postgres.ci4darskkd34.eu-central-1.rds.amazonaws.com'
port=5432
database='tempdb'
username='linearity-home-assignment-user'
password='e0a1bf24bb7a81de7ac81834343ad6169711366863e0f6d66f71f2280e314668'

# Create db connection engine
try:
    engine = create_engine(f"postgresql+psycopg2://{username}:{password}@{host}:{port}/{database}")
except Exception as e:
    print(e)

df_users_app = pd.read_sql(sql='select * from public.users', con=engine)
```

### 2: Python Code to access the accounts data csv from S3 bucket & copy its contents in Google sheet/csv.
---
```python
# S3 bucket params
bucket_name = 'data-temp-bucket'
region = 'eu-central-1'
file_name = 'account_users.csv'

# Load csv from S3, save to df
try:
    df_users_be = pd.read_csv(f"s3://{bucket_name}/{file_name}")
except Exception as e:
    print(e)
```

### 3: Upload Data to BI Solution

###### Steps
- Exported dataFrames to csv and saved locally
- Created tables and imported data into a personal Redshift datacase running on an EC2 cluster
- Created Metabase Instance > Connected Redsfhit Database > Created Dashboard

###### Viewing Metabase Dashboard
- Metabase Link: https://max-learning.metabaseapp.com/dashboard/8-linearity-task-dashboard
- To view Dashboard in Metabase, please email: max.schlafli@gmail.com
- Dashboard PDF has been saved in this repo
  
