# Mapreduce Python Example
This is a python implementation of mapreduce paradigm. This project uses two `.csv` files containing various information about different companies, to generate a `.json` file with the condensed information of each company.
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
All the `.json` files are outputs.
