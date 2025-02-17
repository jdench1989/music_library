# Albums Model and Repository Classes Design Recipe

_Copy this recipe template to design and implement Model and Repository classes for a database table._

## 1. Design and create the Table

Table: albums

Columns:
id | title | release_year | artist_id


## 2. Create Test SQL seeds

seeds/music_library.sql

## 3. Define the class names

Usually, the Model class name will be the capitalised table name (single instead of plural). The same name is then suffixed by `Repository` for the Repository class name.

```python
# Table name: albums

# Model class
# (in lib/album.py)
class Album


# Repository class
# (in lib/album_repository.py)
class AlbumRepository

```

## 4. Implement the Model class

Define the attributes of your Model class. You can usually map the table columns to the attributes of the class, including primary and foreign keys.

```python
# Table name: albums

# Model class
# (in lib/album.py)

class Album:
    def __init__(self):
        self.id = 0
        self.title = ""
        self.release_year = ""
        self.artist_id = None


```

## 5. Define the Repository Class interface

Your Repository class will need to implement methods for each "read" or "write" operation you'd like to run against the database.

Using comments, define the method signatures (arguments and return value) and what they do - write up the SQL queries that will be used by each method.

```python
# Table name: albums

# Repository class
# (in lib/album_repository.py)

class AlbumRepository():

    def all():
        # Selecting all records
        # Arguments:
        #   None
        # Returns: 
        #   An array of Student objects.
        # Executes the SQL query:
        #   SELECT id, title, release_year, artist_id FROM albums;


```

## 6. Write Test Examples

Write Python code that defines the expected behaviour of the Repository class, following your design from the table written in step 5.

These examples will later be encoded as Pytest tests.

```python

# 1
# Get all albums

repo = AlbumRepository()

albums = repo.all()

len(albums) # =>  12

albums[0].id # =>  1
albums[0].title # =>  'Doolittle'
albums[0].release_year # =>  1989
albums[0].artist_id # => 1

albums[-1].id # =>  12
albums[-1].title # =>  'Ring Ring'
albums[-1].release_year # =>  1973
albums[-1].artist_id # => 2

```

Encode this example as a test.


## 7. Test-drive and implement the Repository class behaviour

_After each test you write, follow the test-driving process of red, green, refactor to implement the behaviour._