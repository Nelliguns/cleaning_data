# Cleaning Data

The data is collected from a Swedish housing marketplace. I collected this data to see if there are some interesting insights I can find within my area of living.

After scraping the data it was in pretty bad shape(some cleaning was even done before exporting the data from scrapy)

Some of the things I had to do was

* Remove new lines, spaces, obscure characters(invisible and so on)
* Remove NaN values
* Extract numeric values from string
* Change data type of columns


### Removing unwanted characters

Had to add invisible characters that where giving me issues to the list of chars to remove.

```python
chars = ["!",'"',"#","%","&","'","(",")","*","+",",","-",".","/",":",";","<","=",">","?","@","[","\\","]","^","_","`","{","|","}","~","–"," "]

for char in spec_chars:
    df['column'] = df['column'].str.replace(char, '')
```

### Remove NaN values

```python
df = df.dropna()
```

### Extract numeric values from string in column

```python
df['column'] = df['column'].str.extract('(\d+)').astype(int)
```

### Change data type of values in columns

```python
df[["column1", "column2", "column3"]] = df[["column1", "column2", "column3"]].apply(pd.to_numeric)
```
