# Mapreduce Implementation in Python
This is a python implementation of mapreduce paradigm. This project uses two files, `companies.csv` and `accounts.csv`, to produce distinct `.json` files for each company information.
## Installation
This project is supposed to run with [Apache hadoop](https://hadoop.apache.org). To run this project, install hadoop first. You can install it using [Homebrew](https://brew.sh/). Run this command:
```
brew install hadoop
```
After installation, move the `.csv` and `.py` files to hdfs directory using this command:
```
hdfs dfs -put local_dir_of_file hdfs_dir_of_file
```
Example:
```
hdfs dfs -put /Users/Ashik/Desktop/Mapreduce/Mappers.py /Mappers.py
```
You can check the contents of hdfs using this command:
```
hdfs dfs -ls /
```
### Running the Project
Then using `hadoop streaming jar`, you can run the mapreduce code. The command is:
```
hadoop jar hadoop_streaming_jar_directory -input -input '/companies.csv' -input '/accounts.csv' -mapper 'python /Mapper.py' -reducer 'python /Reducer.py' -output /output
```
To find `hadoop streaming jar`, use this command:
```
find / -name 'hadoop-streaming*.jar'
```
### Output
The output will be generated in a folder named `output` inside hdfs. Copy the `output` folder to your local using this command:
```
hdfs dfs -get /output desired_local_directory
```
All the `.json` files are outputs. Sample output:
```
{
  "orgno": 5560006628,
  "company_name": "KFUK-KFUM:s i Eskilstuna Fastighetsaktiebolag",
  "phone_number": "016-144370",
  "sni_code": 68320,
  "sni_text": "Fastighetsförvaltare på uppdrag",
  "accounts": [
    {
      "date_from": "2012-01-01",
      "date_to": "2012-12-31",
      "profit_margin_percent": 45.09,
      "net_operating_income": 967
    },
    {
      "date_from": "2013-01-01",
      "date_to": "2013-12-31",
      "profit_margin_percent": -15.16,
      "net_operating_income": 488
    },
    {
      "date_from": "2014-01-01",
      "date_to": "2014-12-31",
      "profit_margin_percent": 32.32,
      "net_operating_income": 1114
    },
    {
      "date_from": "2015-01-01",
      "date_to": "2015-12-31",
      "profit_margin_percent": 29.23,
      "net_operating_income": 1372
    },
    {
      "date_from": "2016-01-01",
      "date_to": "2016-12-31",
      "profit_margin_percent": 31.86,
      "net_operating_income": 1130
    }
  ]
}
