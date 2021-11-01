# Class Database

## Submission

Below you will find a set of tasks for you to complete to set up a databases of students and mentors.

To submit this homework write the correct commands for each question here:

```sql


```

When you have finished all of the questions - open a pull request with your answers to the `Databases-Homework` repository.

## Task

1. Create a new database called `cyf_classes` (hint: use `createdb` in the terminal)
 cd createdb
 
2. Create a new table `mentors`, for each mentor we want to save their name, how many years they lived in Glasgow, their address and their favourite programming language.
```--create mentor table
CREATE TABLE mentor(
id  	SERIAL PRIMARY KEY,
name 	VARCHAR(30) NOT NULL,
years_lived_in_Glasgow 	INT,
address  			VARCHAR(120) NOT NULL,
favourite_programming_language  VARCHAR(30) NOT NULL
);
```

 
3. Insert 5 mentors in the `mentors` table (you can make up the data, it doesn't need to be accurate ;-)).
```--Insert data in mentor table

INSERT INTO mentor (name, years_lived_in_Glasgow, address, favourite_programming_language) VALUES ('Abishek', 3,  'Mumbai', 'JavaScript');
INSERT INTO mentor (name, years_lived_in_Glasgow, address, favourite_programming_language) VALUES ('Harry', 5,  'Spain', 'Apex');
INSERT INTO mentor (name, years_lived_in_Glasgow, address, favourite_programming_language) VALUES ('Mani', 2,  'UK', 'C++');
INSERT INTO mentor (name, years_lived_in_Glasgow, address, favourite_programming_language) VALUES ('Anita', 2,  'USA', 'C');
INSERT INTO mentor (name, years_lived_in_Glasgow, address, favourite_programming_language) VALUES ('Payal', 6,  'Pune', 'JavaScript');
```
4. Create a new table `students`, for each student we want to save their name, address and if they have graduated from Code Your Future.
 ```--Insert data in students table 

CREATE TABLE students(
id SERIAL PRIMARY KEY,
name VARCHAR(30) NOT NULL,
address  VARCHAR(120) NOT NULL,
CYF  VARCHAR(30)
);
```
5. Insert 10 students in the `students` table.
 ```--Insert data in students table

INSERT INTO students (name, address, CYF) VALUES ('Abby', 'Mumbai', 'Yes');
INSERT INTO students (name, address, CYF) VALUES ('Dani', 'Pune', 'Yes');
INSERT INTO students (name, address, CYF) VALUES ('Elena', 'Chandigarh', 'Yes');
INSERT INTO students (name, address, CYF) VALUES ('Mansi', 'Shimla', 'Yes');
INSERT INTO students (name, address, CYF) VALUES ('Kanti', 'Luckhnow', 'No');
INSERT INTO students (name, address, CYF) VALUES ('Preeti', 'MAdrid', 'Yes');
INSERT INTO students (name, address, CYF) VALUES ('Vinitha', 'Girona', 'No');
INSERT INTO students (name, address, CYF) VALUES ('Maiya', 'Velencia', 'Yes');
INSERT INTO students (name, address, CYF) VALUES ('Parul', 'London', 'No');
INSERT INTO students (name, address, CYF) VALUES ('Jasmeen', 'Madrid', 'Yes');
```

6. Verify that the data you created for mentors and students are correctly stored in their respective tables (hint: use a `select` SQL statement).
```selecr * from mentor;
selecr * from students;

```
7. Create a new `classes` table to record the following information:

   - A class has a leading mentor
   - A class has a topic (such as Javascript, NodeJS)
   - A class is taught at a specific date and at a specific location

```--create classes table

CREATE TABLE classes (
  id               SERIAL PRIMARY KEY,
  mentor_id      INT REFERENCES mentor(id),
  topic         VARCHAR(120) NOT NULL,
  date          DATE NOT NULL,
  location      VARCHAR(120) NOT NULL
);
```
8. Insert a few classes in the `classes` table
--Insert data in classes table

INSERT INTO classes (mentor_id, topic, date, location) VALUES (1, 'JavaScript', '2019-10-01', 'Mumbai');
INSERT INTO classes (mentor_id, topic, date, location) VALUES (2, 'Nodes', '2019-10-05', 'Barcelona');
INSERT INTO classes (mentor_id, topic, date, location) VALUES (4, 'JavaScript', '2019-10-03', 'USA');
```

9. We now want to store who among the students attends a specific class. How would you store that? Come up with a solution and insert some data if you model this as a new table.
--Insert data in classes table

INSERT INTO classes (mentor_id, topic, date, location) VALUES (1, 'JavaScript', '2019-10-01', 'Mumbai');
INSERT INTO classes (mentor_id, topic, date, location) VALUES (2, 'Nodes', '2019-10-05', 'Barcelona');
INSERT INTO classes (mentor_id, topic, date, location) VALUES (4, 'JavaScript', '2019-10-03', 'USA');
```

11. Answer the following questions using a `select` SQL statement:
    - Retrieve all the mentors who lived more than 5 years in Glasgow
     SELECT * FROM mentor WHERE years_lived_in_Glasgow > 5;
     
    - Retrieve all the mentors whose favourite language is Javascript
      SELECT * FROM mentor WHERE favourite_programming_language = 'JavaScript';

    - Retrieve all the students who are CYF graduates
      SELECT * FROM students WHERE CYF = 'Yes';

    - Retrieve all the classes taught before June this year
      SELECT * FROM classes WHERE date < '2019/06/01'

    - Retrieve all the students (retrieving student ids only is fine) who attended the Javascript class (or any other class that you have in the `classes` table).
      SELECT *  FROM classesAttender Where classes_id = 1;
      
