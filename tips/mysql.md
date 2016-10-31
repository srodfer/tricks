![pic_mys](https://upload.wikimedia.org/wikipedia/en/6/62/MySQL.svg)

###Usual commands: 
Create a Database
```
mysql> CREATE DATABASE database_name;
```
Drop a Database
```
mysql> DROP DATABASE [IF EXISTS] database_name;
```
Create table
```
mysql> CREATE TABLE table_name (field_name1 VARCHAR(20), field_name2 CHAR(1), field_name3 DATE);
```
Truncate table
```
mysql> TRUNCATE TABLE table_name;
```
Load data to table from file
```
mysql> LOAD DATA INFILE '/path/to/file/' INTO TABLE table_name;
```
Export data to file (fields separated by ',' and lines terminated with '\n')
```
mysql> SELECT col1 INTO OUTFILE '/path/to/file'
-> FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
-> LINES TERMINATED BY '\n'
-> FROM table_name;
```
Insert data into table
```
mysql> INSERT INTO table_name VALUES ('value1','value2','date1',NULL);
```
Update rows
```
mysql> UPDATE table_name SET field_name = 'value1' WHERE field_name2 = 'value2';
```
Delete rows
```
mysql> DELETE FROM table_name WHERE field_name2 = 'value2';

```

###JOIN syntax
```
mysql> SELECT t1.name, t2.salary
  FROM employee AS t1 INNER JOIN info AS t2 ON t1.name = t2.name;
```

###Common queries
- The Row Holding the Maximum of a Certain Column
```
mysql> SELECT article, dealer, price FROM shop
WHERE price=(SELECT MAX(price) FROM shop);
```
- Maximum of Column per Group
```
mysql> SELECT article, MAX(price) AS price FROM shop GROUP BY article;
```

###Getting Information About Databases and Tables and more
```
mysql> SELECT USER();
```
```
mysql> SELECT DATABASE();
```
```
mysql> DESCRIBE pet;
```
```
mysql> SELECT user,host from mysql.user;
```
```
mysql> SHOW PROCEDURE STATUS;
```
```
mysql> SHOW FUNCTION STATUS;
```

###MySQL dump
To make a backup of an entire database:
```
$ mysqldump -u user -p  [options] DB_NAME > db_dump.sql
```
To load the dump file back into the server:
```
$ mysql DB_NAME < db_dump.sql
```
Mysqldump will backup by default all the triggers but NOT the stored procedures/functions. To include in an existing backup script also the triggers and stored procedures
```
$ mysqldump -u user -p --routines DB_NAME > db_dump.sql
```
To backup ONLY the stored procedures and triggers and not the mysql tables and data
```
$ mysqldump --routines --no-create-info --no-data --no-create-db --skip-opt <database> > outputfile.sql
```

###Batch Mode
```
$ mysql -h host-u user-p < batch-file
```
```
mysql < batch-file> mysql.out
```
Execute script within client MySQL and save output to file
```
mysql> tee path/to/file.out
mysql> \. script.sql
```

###MySQL Change a User Password
```
1. Login as a root user
2. mysql> use mysql;
3. mysql> SET PASSWORD FOR 'user-name-here'@'hostname-name-here' = PASSWORD('new-password-here');
```
or
```
3. mysql> UPDATE mysql.USER SET Password=PASSWORD('foobar') WHERE USER='tom' AND Host='localhost';
```

###Character set and Collation
Find out default character set for a database
```
mysql> SELECT default_character_set_name FROM information_schema.SCHEMATA WHERE schema_name = database_name;
```
Find out character set and collation used:
```
mysql> show variables like "%character%";
```
```
mysql> show variables like "%collation%";
```
Dumping a database specifying the character set (utf8)
```
$ mysqldump -u user -p --default-character-set=utf8 --result-file=db_dump.sql DB_NAME
$ mysql -u user -p --default-character-set=utf8 DB_NAME < db_dump.sql
```
Modify character set in database and table
```
mysql>  ALTER DATABASE TRP_DEV CHARACTER SET utf8 COLLATE utf8_unicode_ci;
mysql>  ALTER TABLE status CONVERT TO CHARACTER SET latin1 COLLATE latin1_general_ci;
```
