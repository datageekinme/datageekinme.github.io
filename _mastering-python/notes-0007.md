---
title: "Python: Files"
permalink: /mastering-python/0007/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.png"
excerpt: "All about files"
toc: true
---

## File I/O

To read a file, we first need to open it in Python.

Following is the file, called `story.txt`, that we will be reading

![Sample File](/assets/images/courses/mastering-python/notes-0007-ss-001.JPG){: .align-center}

### `open`

To open a file we use the `open` keyword as shown below:

```python
>>> f = open("story.txt")

>>> f
<_io.TextIOWrapper name='story.txt' mode='r' encoding='cp1252'>
```

### `read`

The `read` method reads the complete file and moves the cursor to the end of the file. Here is an example:

```python
>>> f.read()
'This is the first line of the short story.\nThis is the second line of the short story.\nThis is the third line of the short story.\nThe end.\n'

>>> f.read()
''
```

### `seek`

As `read` combs through the entire file, the cursor gets moved to the end. In case, you need to read through the same file again, you would need to move the cursor back up. This can be done using the `seek` method as follows:

```python
>>> f.seek(0)
0

>>> f.read()
'This is the first line of the short story.\nThis is the second line of the short story.\nThis is the third line of the short story.\nThe end.\n'

>>> f.read()
''
```

### `readline`

`readline` can be used to return one line at a time.

```python
>>> f.seek(0)
0

>>> f.readline()
'This is the first line of the short story.\n'

>>> f.readline()
'This is the second line of the short story.\n'

>>> f.readline()
'This is the third line of the short story.\n'

>>> f.readline()
'The end.\n'

>>> f.readline()
''
```

### `readlines`

Returns a list of strings, with each string being a line. For example:

```python
>>> f.seek(0)
0

>>> f.readlines()
['This is the first line of the short story.\n', 'This is the second line of the short story.\n', 'This is the third line of the short story.\n', 'The end.\n']
```

### `close`

Once the file is opened, the connection stays until it's explicitly closed. To close a file, you can use the `close` method as follows:

```python
>>> f.closed
False

>>> f.close()

>>> f.closed
True

>>> f.read()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: I/O operation on closed file.
```

**NOTE:** Always close files - it frees up system resources

### `with` Blocks

The previous option of a opening, reading and then closing of the file can be simplified using the `with` keyword as follows:

```python
>>> with open('story.txt') as file:
...     file.read()
...
'This is the first line of the short story.\nThis is the second line of the short story.\nThis is the third line of the short story.\nThe end.\n'

>>> file.closed
True
```
`with` handles file closing automatically.

### `write`

In order to write to files, you still need to open the file. Need to specify the `"w"` flag as the second argument.

```python
>>> with open('another-story.txt', 'w') as file:
...     file.write('This is the first line of the story.\n')
...     file.write('This is the second line of the story.\n')
...     file.write('The end.\n')
...
37
38
9
```

If you run again, the file is just overwritten. In case the file written to doesn't exist, it gets created.

## File Modes

| Character | Meaning |
| --- | --- |
| 'r' | open for reading (default) |
| 'w' | open for writing, truncating the file first |
| 'x' | open for exclusive creation, failing if the file already exists |
| 'a' | open for writing, appending to the end of the file if it exists. Always appends to the end of the file, even if cursor is set to start of file using `seek` |
| 'b' | binary mode |
| 't' | text mode (default) |
| '+' | open a disk file for updating (reading and writing) |
| 'U' | universal newlines mode (deprecated) |

## Reading CSV files

### `reader`

Lets you iterate over rows of the CSV as lists.

```python
>>> from csv import reader
>>> with open('nypd_complaint_data_current_ytd.csv') as file:
...     data = reader(file)
...     for row in data:
...             print(row)
...
...
['CMPLNT_NUM', 'ADDR_PCT_CD', 'BORO_NM', 'CMPLNT_FR_DT', 'CMPLNT_FR_TM', 'CMPLNT_TO_DT', 'CMPLNT_TO_TM', 'CRM_ATPT_CPTD_CD', 'HADEVELOPT', 'HOUSING_PSA', 'JURISDICTION_CODE', 'JURIS_DESC', 'KY_CD', 'LAW_CAT_CD', 'LOC_OF_OCCUR_DESC', 'OFNS_DESC', 'PARKS_NM', 'PATROL_BORO', 'PD_CD', 'PD_DESC', 'PREM_TYP_DESC', 'RPT_DT', 'STATION_NAME', 'SUSP_AGE_GROUP', 'SUSP_RACE', 'SUSP_SEX', 'TRANSIT_DISTRICT', 'VIC_AGE_GROUP', 'VIC_RACE', 'VIC_SEX', 'X_COORD_CD', 'Y_COORD_CD', 'Latitude', 'Longitude', 'Lat_Lon']
['831526991', '67', 'BROOKLYN', '03/31/2018', '23:30:00', '03/31/2018', '23:37:00', 'COMPLETED', '', '', '0', 'N.Y. POLICE DEPT', '236', 'MISDEMEANOR', '', 'DANGEROUS WEAPONS', '', 'PATROL BORO BKLYN SOUTH', '782', 'WEAPONS, POSSESSION, ETC', 'STREET', '03/31/2018', '', '', '', '', '', 'UNKNOWN', 'UNKNOWN', 'E', '1003227', '177460', '40.653751263', '-73.931609227', '(40.653751263, -73.931609227)']
```

### `DictReader`

Lets you iterate over rows of the CSV as OrderedDicts.

```python
>>> from csv import DictReader
>>> with open('nypd_complaint_data_current_ytd.csv') as file:
...     data = DictReader(file)
...     for row in data:
...             print(row)
...
OrderedDict([('CMPLNT_NUM', '831526991'), ('ADDR_PCT_CD', '67'), ('BORO_NM', 'BROOKLYN'), ('CMPLNT_FR_DT', '03/31/2018'), ('CMPLNT_FR_TM', '23:30:00'), ('CMPLNT_TO_DT', '03/31/2018'), ('CMPLNT_TO_TM', '23:37:00'), ('CRM_ATPT_CPTD_CD', 'COMPLETED'), ('HADEVELOPT', ''), ('HOUSING_PSA', ''), ('JURISDICTION_CODE', '0'), ('JURIS_DESC', 'N.Y. POLICE DEPT'), ('KY_CD', '236'), ('LAW_CAT_CD', 'MISDEMEANOR'), ('LOC_OF_OCCUR_DESC', ''), ('OFNS_DESC', 'DANGEROUS WEAPONS'), ('PARKS_NM', ''), ('PATROL_BORO', 'PATROL BORO BKLYN SOUTH'), ('PD_CD', '782'), ('PD_DESC', 'WEAPONS, POSSESSION, ETC'), ('PREM_TYP_DESC', 'STREET'), ('RPT_DT', '03/31/2018'), ('STATION_NAME', ''), ('SUSP_AGE_GROUP', ''), ('SUSP_RACE', ''), ('SUSP_SEX', ''), ('TRANSIT_DISTRICT', ''), ('VIC_AGE_GROUP', 'UNKNOWN'), ('VIC_RACE', 'UNKNOWN'), ('VIC_SEX', 'E'), ('X_COORD_CD', '1003227'), ('Y_COORD_CD', '177460'), ('Latitude', '40.653751263'), ('Longitude', '-73.931609227'), ('Lat_Lon', '(40.653751263, -73.931609227)')])
```

### Other Delimiters

Reader accepts a 'delimiter' kwarg in case your data isn't separated by commas.

```python
>>> from csv import DictReader
>>> with open('nypd_complaint_data_current_ytd.csv') as file:
...     data = reader(file, delimiter="|") # <== delimiter passed Here
...     # above can be DictReader as well
...     for row in data:
...             print(row)
...
```

## Writing CSV files

There are nmainly 2 ways to write data to a CSV file:
* Using lists the following 2 commands are used:
  * `writer`
  * `writerow`
* Using dictionaries
  * `DictWriter`

### `writer` and `writerow`

Creates a writer object for writing to CSV

```python
>>> from csv import writer
>>> with open('write_test.csv', 'w') as file:
...     data = writer(file)
...     data.writerow(['Name', 'Age'])
...     data.writerow(['John', 30])
...     data.writerow(['Jane', 29])
...
10
9
9
```
### `DictWriter`

Creates a writer object for writing using dictionaries.

`fieldnames` are used as kwarg for the DictWriter to specify the headers. `writeheader` method on a writer is used to write the header row and `writerow` method to write a row based on a dictionary.

```python
>>> from csv import DictWriter
>>> headers = ['FirstName', 'LastName', 'Age']
>>>
>>> from csv import DictWriter
>>> with open('write_test_dict.csv', 'w') as file:
...     headers = ['FirstName', 'LastName', 'Age']
...     data = DictWriter(file, fieldnames=headers)
...     data.writeheader()
...     data.writerow({'FirstName': 'John', 'LastName': 'Smith', 'Age': 53})
...     data.writerow({'FirstName': 'Jane', 'LastName': 'Smith', 'Age': 48})
...
15
15
``` 



[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
