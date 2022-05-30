import csv
import os
import pandas as pd

#Gather the fisrt docuemtns and convert them to a dataframe and check for duplicates
#Deliever the before and after results.

#FIRST DOCUMENT
print("Reading first file...")
file_one = pd.read_csv('/Users/SamuelMalkasian/Desktop/File_One_2020.csv')

total_names_d1 = file_one.duplicated().sum()
print(f"There are: ({total_names_d1}) TOTAL names in the 2020 document")

total_unique_names_d1 = (~file_one.duplicated()).sum()
print(f"There are: ({total_unique_names_d1}) UNIQUE names in the 2020 document")


#SECOND DOCUMENT
print("\nReading second file...")
file_two = pd.read_csv('/Users/SamuelMalkasian/Desktop/File_Two_2021.csv')

total_names_d2 = file_two.duplicated().sum()
print(f"There are: ({total_names_d2}) TOTAL names in the 2021 document")

total_unique_names_d2 = (~file_two.duplicated()).sum()
print(f"There are: ({total_unique_names_d2}) UNIQUE names in the 2021 document\n")


####################### REMOVE THE DUPLICATE NAMES AND EXPORT TO NEW CSV(S)


#Document ONE:
file_output_one = "/Users/SamuelMalkasian/Desktop/File_One_2020_Edited.csv"

file_one = pd.read_csv('/Users/SamuelMalkasian/Desktop/File_One_2020.csv')

file_one.drop_duplicates(subset=None, inplace=True)

file_one.to_csv(file_output_one, index=False)

#Document TWO:
file_output_two = "/Users/SamuelMalkasian/Desktop/File_Two_2021_Edited.csv"

file_two = pd.read_csv('/Users/SamuelMalkasian/Desktop/File_Two_2021.csv')

file_two.drop_duplicates(subset=None, inplace=True)

file_two.to_csv(file_output_two, index=False)


#convert the exported documents BACK as a DataFrame, concatinate, and then run them through the
#duplicate removal and counter again.

df1 = pd.read_csv('/Users/SamuelMalkasian/Desktop/File_One_2020_Edited.csv')
df2 = pd.read_csv('/Users/SamuelMalkasian/Desktop/File_Two_2021_Edited.csv')


both_docs = [df1, df2]

results = pd.concat(both_docs)

df1_added = len(df1)
df2_added = len(df2)

total_added = df1_added + df2_added
print(f"There are a total of ({total_added}), when adding both UNIQUE names up (from 2020 & 2021).\n")

final_result = (~results.duplicated()).sum()
#print(f"After removing the caryover names from 2020 to 2021, there are, ({final_result}) names left.\n")

new_doner = total_added - final_result
caryover_doners = total_unique_names_d2 - new_doner
print(f"({new_doner}) people donated for the first time in 2021 and ")
print(f"({caryover_doners}) donated again in 2021\n")

quotient = int(caryover_doners) / int(total_names_d1)
rate_of_retention = quotient * 100
print(f"The rate of retention is {rate_of_retention}")
