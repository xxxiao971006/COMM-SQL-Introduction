# Data Definition Language (DDL)

In this section, we will cover the following DDL commands and create a new [schema](glossary.md) and a new table in MySQL:

- `CREATE`
- `ALTER`
- `DROP`

By the end of this section, you will have a good understanding of how to use these commands to create, alter and drop your database structure effectively.

## CREATE Command

The CREATE command is used to create new objects in sql such as schemas, tables, indexes and constraints. Instead of using both mouse and keyboard to create schema, this time we will use only keyboard and type our commands in a [query script_](glossary.md) to create a new schema and table. Let's open MySQL Workbench and get started 🔥!

1.  Open Local instance MySQL80 by single clicking the MySQL80 rectangle.

    ![Local instance MySQL80](images/Local_instance_MySQL80.png){ width="300" }

2.  Click the "new SQL file" button on the left corner of your Workbench.

    ![New Query](images/New_Query.png){ width="300" }

    This will give us a query text window where we can type our SQL commands.

    ![Query text window](images/query_text_window.png){ width="350" }

3.  Type the commands below in your query text window:

    ```sql
    CREATE DATABASE intro_to_sql;
    ```

    !!!Note inline end "Execute Buttons ![Execute Icons](images/execute_icon.png)"
        **Execute button** ![Execute Icons](images/execute_all.png) is used to execute all the commands in the sql file.

        **Cursor Execute button** ![Execute Icons](images/execute_one.png) is used to to run a single command where the keyboard cursor is. The keyboard shortcut for this is CTRL + Enter on Windows or CMD+Enter (⌘+Enter) on Mac.

4.  Click Execute button ![Execute Icons](images/execute_one.png).

    After execute a success message will display in the "Output" section on the bottom of your Workbench.

    ![success message](images/create_db_success_message.png){ width="400" }

5.  Click the refresh button on the right corner of the navigator to make sure the new database is added to your SCHEMAS list.

    ![refresh schema](images/refresh_db.png){ width="300" }

6.  Type the commands below and execute it to set "intro_to_sql" as the default schema:

    ```sql
    USE intro_to_sql;
    ```

    The default schema will be bolded in your schema list.

    ![bold default db](images/bold_default_db.png){ width="250" }

Congratulations 🎉! You have successfully created a new schema "intro_to_sql". Next, let's add a new table to our new schema.

### CREATE Table

In this example, we will create a table named "employee" with five columns: "EMP_ID", "FIRST_NAME", "LAST_NAME", "SALARY" and "BONUS". The "EMP_ID" column is the primary key, and other columns are required (NOT NULL).

Type and execute the commands below:

```sql
CREATE TABLE `employee` ( --(1)
  `EMP_ID` INT NOT NULL AUTO_INCREMENT, --(2)
  `FIRST_NAME` VARCHAR(45) NOT NULL, --(3)
  `LAST_NAME` VARCHAR(45) NOT NULL,
  `SALARY` INT NOT NULL, --(4)
  `BONUS` INT NOT NULL,
  PRIMARY KEY (`EMP_ID`) --(5)
);
```

1. This line of code will name the new table as "employee".
2. This code will make a column called "EMP_ID" that's an integer (INT), required (NOT NULL), and increases automatically(AUTO_INCREMENT).
3. This code will make a column called "FIRST_NAME" that's a string with length <=45 ([VARCHAR(45)](glossary.md)) and can't be empty.
4. This code will make a column called "SALARY" that's an integer and can't be empty.
5. This code will set "EMP_ID" as primary key.

Refresh schema list in the navigator, and you will see the employee table under "intro_to_sql" schema. And a success message is shown in the "Output" section.

![new table created](images/table_created.png){ width="500" }

Good Job 🎉! You just created a new table using DDL CREATE command.

??? Note

      In SQL, by default, most commands are not case sensitive. This means that you can use uppercase or lowercase letters interchangeably when writing commands or queries, and SQL will treat them the same way.

      For example, the following two queries are equivalent:

**insert little reference inside code!**

The "id" column is the primary key, and the "name" column is required (NOT NULL).

1. Click Execute icon.

In this example, we are creating a table named "customers" with four columns: "id", "name", "email", and "age". The "id" column is the primary key, and the "name" column is required (NOT NULL).

## ALTER Command

The ALTER command is used to modify the structure of existing database objects. It can add, delete, or modify columns and constraints in a table. In the example below, we will use ALTER to add columns to "employee" table.

Type and execute the commands below:

```sql
ALTER TABLE employee
ADD AGE INT,
ADD BIRTH_DATE DATE;
```

You've added an "AGE" column and a "BIRTH_DATE" column to your employee table.

![age and birthdate columns added](images/age_bd_column.png){ width="400" }

## DROP Command

The DROP command is used to remove existing database objects such as databases, tables, indexes, and constraints.

Type and execute the command below:

```sql
ALTER TABLE employee
DROP COLUMN BIRTH_DATE,
DROP COLUMN AGE;
```

In this example, we deleted both "AGE" column and "BIRTH_DATE" column in "employee" table.

![dropped age and birthdate columns](images/drop_age_bd.png){width="400"}

Now let's try some dangerous commands. Create a new schema called "test_drop", set it as default, and create a table called "test" in this schema.

```sql
CREATE DATABASE test_drop;
USE test_drop;
CREATE TABLE `test` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `description` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`id`)
);
```

Then type and execute the command below:

```sql
DROP DATABASE test_drop;
```

Your "test*drop" schema including the "test" table is permanently deleted without any warning message* when you execute the above command.

!!! danger

       DROP DATABASE command deletes the database and all its tables and data. It will delete the specified object _permanently_, so use it with caution.

## Conclusion

We hope this section has been helpful with your learning journey on the following:

- [x] Using CREATE to create a new database objects such as schema, table and column
- [x] Using USE to set a schema to default
- [x] Using ALTER to modify the database objects
- [x] Using DROP to delete database objects

In the next section, we will go through SQL DML commands, which are used to manipulate data in the database. With these commands, you can retrieve, insert, update, and delete data from your database.

Let's continue learning! 👉 **[DML](DML.md)**
