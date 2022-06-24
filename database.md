_During this documentation, when I mention a "key", I'm talking about the column name, such as "Name", and when I mention "value", I'm talking about the value of that column within the row, such as "Seailz"_

## Getting Started
There are two ways to create a new database instance:

### MySQL
```java
Database db = new Database(
                "INSERT IP",
                3306,
                "INSERT USERNAME",
                "INSERT PASSWORD",
                "INSERT DATABASE NAME");
```
### SQLite

```java
Database db = new Database(file);
```

The code will automatically make a JDBC connection URL for you.
Connect to the database with:
```java
db.connect(); 
```

## Creating A Table
To choose what kind of data our columns are, create a new Column instance and add the following parameters. You can add these Column instances to an ArrayList in order to create multiple columns.

```java
List<Column> columns = new ArrayList<>();
        
        Column column = new Column(ColumnType.VARCHAR, "Test Column");

        columns.add(column);
```

<summary> Custom Lengths </summary>

#### Custom Column Lengths
```java
column.setLength(INSERT_LENGTH_HERE);
```
<summary> Disallow Null </summary>

To disallow null in a column, do this:
```java
column.setAllowNull(false); // (by default this is set to true)
```

#### Current datatypes:
```java
    VARCHAR,
    INT,
    DOUBLE,
    BOOLEAN,
    BIGINT,
    FLOAT,
    LONG,
    BYTE,
    DECIMAL,
    BLOB,
    TINYINT
```

### Saving and Reading Java Objects

#### Reading Objects:
To read objects from a database, it's quite complicated.

First, you'll need to annotate the constructor in your object that you wish to use with `@DatabaseConstructor`
Next, for every parameter in your constructor, you'll need to add a `@Column (INSERT_COLUMN_NAME)` annotation.

<p></p>
By now, your constructor should look kind of like this

```java
@DatabaseConstructor
public TestObject(@Column("profileName") String profileName) {
    // DO SOMETHING
}
```

`PLEASE NOTE: Both of these annotations are required. If they aren't included, the framework will throw an exception.`

Great! Now we are ready to actually start reading! Here's how:
```java
TestObject testObject = (TestObject) db.readObject("INSERT_TABLE", "INSERT_KEY", "INSERT_VALUE", TestObject.class);
```

#### Saving Objects:
Luckily, it's pretty simple to save objects.
<p>Here's an example:</p>

```java
db.saveObject(testObject, "INSERT_TABLE");
```


### Creating a table instance
```java
Table table = new Table(
                "fooTable",
                columns
        );
```

  <summary>Primary Key</summary>
  If you wish to set a primary key, you can use this:

  ```java
   table.setPrimaryKey("INSERT PRIMARY KEY NAME HERE");
```

Great! Now, all there is left to do is tell the database to create this table. You can do that like this:

```java
db.createTable(table);
```

There you go! You should now have a table inside of your database.

## Transactions _IMPORTANT_
Before we move on I want to leave an important note. Transactions are an essential part of working on a database and make sure you don't make any errors. Here's how to use them:

### Starting a transaction
```java
db.startTransaction();
```

### Committing a transaction
```java
 db.commit();
```

### Rolling back a transaction
```java
db.rollback();
```

## Reading from the database
### Reading from a database
```java
db.get("INSERT_TABLE_NAME_HERE", "INSERT_KEY_HERE", "INSERT_VALUE_HERE", "INSERT_COLUMN_NAME_HERE");
```

Here's a more detailed explanation of what these parameters mean:

```txt
For example, if you wanted to get the details about a player,
the key parameter would be "name" or whatever it is within your table
and the value parameter would be the player's name of whom you wish to get the details.

The "column" parameter would be the specific detail you'd like to get. For example,
if my table contained an "age" column, and I wanted to get the player's age,
I'd set the column parameter to "age"
```

## Inserting Into A Database
This is also pretty easy. All you have to do is make a HashMap of your keys, and values, like this:

```java
 HashMap<String, String> values = new HashMap<>();
        values.put("UUID", "epic uuid!");
        values.put("NAME", "SEAILZ");
```

Once you've done that, this is all you need to do:
```java
db.insert("INSERT_TABLE_NAME_HERE", values);
```

## Check if a table exists
Incredibly easy:
```java
db.tableExists("INSERT_TABLE_NAME_HERE");
```

## Deleting from the database
Also pretty easy:
```java
db.delete("INSERT_TABLE_NAME_HERE", "INSERT_KEY_HERE", "INSERT_VALUE_HERE");
```

## Checking if a row exists
```java
db.rowExists("INSERT_TABLE_HERE", "INSERT_KEY_HERE", "INSERT_VALUE_HERE");
```

## Sending your queries
There's a custom class called "Statement" which can be used to send statements to your database with ease. All you need to do is this:

```java
Statement s = new Statement("INSERT_MYSQL_QUERY_HERE", db.getConnection();
```

Now to execute the command, you have two options:

<summary> With Results Set </summary>
This should be used if the command is supposed to return some results. Here's his:

```java
ResultsSet r = s.executeWithResults();
```
<summary> Without Results Set </summary>
**! Should be used when the command is not expected to return results. For example, creating a new table.**

```java
s.execute();
```


## Disconnecting
Once your are done interacting with your database, be sure to disconnect like this:
```java
db.disconnect();
```

Other than that there are a bunch of other weird and wonderful things added to the database class, so make sure to check it out! It has about every single MySQL command I could find! (thanks copilot). Here's a few highlights

- Exporting and importing from a CSV file
- Counting the amount of rows in a table
- Altering columns

#### This documentation was created by Joee, modified by Seailz
#### This util was created by Seailz
