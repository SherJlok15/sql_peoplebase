# Peoplebase

Here are eight famous people: 

| Id | First Name | Last Name | Year of Birth | Year of Death |
|----|------------|-----------|---------------|---------------|
| 1  | Marilyn    | Monroe    | 1926          | 1962          |
| 2  | Abraham    | Lincoln   | 1809          | 1865          |
| 3  | Nelson     | Mandela   | 1918          | 2013          |
| 4  | Winston    | Churchill | 1874          | 1965          |
| 5  | Bill       | Gates     | 1955          | –             |
| 6  | Charles    | Darwin    | 1809          | 1882          |
| 7  | Pele       | –         | 1940          | –             |
| 8  | Fidel      | Castro    | 1926          | –             |

1. Using your favorite DB client, design and create a database table called `people` that would store the information presented above (create a database first if you don’t have any existing ones to play with). Don’t bother with creating any keys or indices for now, just create the five columns. Copy and paste the SQL query generated by the client below (it should start with `create table` or something similar; if it is difficult to find the query generated by your client, ask for assistance):

    ```postgresql
     create table people_base
    (
    	id int,
    	first_name text,
    	last_name text,
    	year_of_birth int,
    	year_of_death int
    );
    ```

2. **Manually** create a query or a series of queries that would fill the table with the information above. Put the query/queries below:

    ```postgresql
    INSERT INTO people_base ("id", "first_name", "last_name", "year_of_birth", "year_of_death")
    VALUES (1, 'Marilyn', 'Monroe', 1926, 1962),
           (2, 'Abraham', 'Lincoln', 1809, 1865),
           (3, 'Nelson', 'Mandela', 1918, 2013),
           (4, 'Winston', 'Churchill', 1874, 1965),
           (5, 'Bill', 'Gates', 1955, null),
           (6, 'Charles', 'Darwin', 1809, 1882),
           (7, 'Pele', null, 1940, null),
           (8, 'Fidel', 'Castro', 1926, null)
 
    ```

3. Create a query that would return everything from the table:

    ```postgresql
    SELECT * FROM people_base
    ```
    
4. Create a query that would return a single row: the person with the ID of 5.

    ```postgresql
    SELECT * FROM people_base WHERE id = 5
    ```

5. Create a query that would return the four people with the following IDs: 1, 3, 7, 8.

    ```postgresql
    SELECT * FROM people_base WHERE id IN (1,3,7,8)
    ```

6. Create a query that would return all the people except the person with the ID of 4 (`Winston Churchill`).

    ```postgresql
    SELECT * FROM people_base WHERE NOT id = 4
    ```

7. Create a query that would select the first names and last names of the people who were born after 1920:

    ```postgresql
    SELECT first_name, last_name FROM people_base WHERE year_of_birth > 1920
    ```
    
8. Create a query that would select the IDs of the living people:

    ```postgresql
  SELECT id FROM people_base WHERE year_of_death IS NULL
    ```
    
9. Create a query that would return the years of birth and the years of death of everyone who has died. The columns should be aliased `b` and `d` respectively.

    ```postgresql
    SELECT year_of_birth AS b, year_of_death AS d FROM people_base WHERE year_of_death IS NOT NULL
    ```
    
10. Create a query that would return the list of all years of birth, without repetition:

    ```postgresql
    SELECT DISTINCT year_of_birth FROM people_base 
    ```

11. Create a query that would select the people with either their first or last name starting with an `M`:

    ```postgresql
    SELECT * FROM people_base WHERE first_name LIKE 'M%' or last_name LIKE 'M%'
    ```

12. Create a query that would select the people with both their first and last name starting with an `M`:

    ```postgresql
    SELECT * FROM people_base WHERE first_name LIKE 'M%' or last_name LIKE 'M%'
    ```
    
13. Create a query that would select all the people except those whose last name starts with a `C`:

    ```postgresql
    SELECT * FROM people_base WHERE NOT last_name LIKE 'C%'
    ```
    
14. Create a query that would select the people whose first name starts with a letter that precedes `M` in the English alphabet:

    ```postgresql
    SELECT * FROM people_base WHERE first_name < 'M%'
    ```
    
15. Create a query that would return all the people sorted by their last name alphabetically:

    ```postgresql
    SELECT * FROM people_base ORDER BY last_name
    ```

16. Create a query that would return the first names of the people sorted in the reverse alphabetical order. The column should be aliased `fn`.

    ```postgresql
    SELECT first_name as fn FROM people_base ORDER BY first_name DESC 
    ```

17. Create a query that would return the people sorted by their year of birth in the descending order, and then (if two or more people share the same year of birth) by their last name alphabetically:

    ```postgresql
    SELECT * FROM people_base ORDER BY year_of_birth DESC, last_name ASC
    ```
    
18. Set everyone’s last name to your last name:

    ```postgresql
    UPDATE people_base SET last_name = 'Hulchuk'
    ```
    
19. Update the first name of everyone who was born before 1900 to your favorite character’s name:

    ```postgresql
    UPDATE people_base SET first_name = 'Holmes'
    WHERE year_of_birth < 1900
    ```
    
20. Add 1 to both the year of birth and year of death for everyone whose ID is less than 5:

    ```postgresql
    UPDATE people_base SET year_of_birth = year_of_birth + 1, year_of_death = year_of_death + 1
    WHERE id < 5
    ```

21. Delete from the table everyone who died before 2000:

    ```postgresql
    DELETE FROM people_base
    WHERE year_of_death < 2000
    ```

22. Delete everyone from the table:

    ```postgresql
    DELETE FROM people_base
    ```
    
Don’t forget to create a pull request.
