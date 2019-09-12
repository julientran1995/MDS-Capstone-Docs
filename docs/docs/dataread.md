# Reading the Data

Attempts to import data into workable variables in python. So far have only worked with a mini sample file instead of actual data file (file too large)

## Normal Method

      import json

      with open('./data/samples.jsonl', 'r') as json_file:
          json_list = list(json_file)

      for json_str in json_list:
          result = json.loads(json_str)
          print(result)     #each result is one line/json object

* Get result of each line as individual dictionary objects
* *Produced character 'u' in the front? apparently this is a notation for unicode type but it annoyingly sticks to the string representation*


## Using Pandas Dataframe

      import pandas as pd
      import numpy as np

      df = pd.read_json("./data/samples.jsonl",
                              lines=True,
                              orient='columns')

      source = pd.DataFrame([md for md in df._source])      #get a dataframe with 3 columns: timestamp/source/user

      location = pd.DataFrame([md for md in source.source])     #location column


* Product a CSV-like structure to work with
* *Too many sub level, data read time will be a nightmare for large file?*
