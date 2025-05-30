# postgre-Sql

Microsoft Windows [Version 10.0.26100.4061]
(c) Microsoft Corporation. All rights reserved.

C:\Users\Minfy.CHILUKURIVASUSR>psql -U postgres
Password for user postgres:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# CREATE USER university_admin WITH PASSWORD 'your_secure_password';
CREATE ROLE
postgres=# CREATE USER Madhu WITH PASSWORD 'Madhu14777';
CREATE ROLE
postgres=# CREATE CREATE DATABASE university_db OWNER Madhu;
ERROR:  syntax error at or near "CREATE"
LINE 1: CREATE CREATE DATABASE university_db OWNER Madhu;
               ^
postgres=# CREATE DATABASE university_db OWNER Madhu;
CREATE DATABASE
postgres=# GRANT ALL PRIVILEGES ON DATABASE university_db TO Madhu;
GRANT
postgres=# \\q
invalid command \
Try \? for help.
postgres=# \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U Madhu -d university_db
Password for user Madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Madhu"

C:\Users\Minfy.CHILUKURIVASUSR>psql -U Madhu -d university_db
Password for user Madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Madhu"

C:\Users\Minfy.CHILUKURIVASUSR>psql -U Madhu -d university_db
Password for user Madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Madhu"

C:\Users\Minfy.CHILUKURIVASUSR>psql -U Madhu -d university_db
Password for user Madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Madhu"

C:\Users\Minfy.CHILUKURIVASUSR>psql -U postgres
Password for user postgres:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# psql -U postgres
postgres-# \du
                                 List of roles
    Role name     |                         Attributes
------------------+------------------------------------------------------------
 madhu            |
 postgres         | Superuser, Create role, Create DB, Replication, Bypass RLS
 university_admin |


postgres-# ALTER ROLE madhu WITH LOGIN PASSWORD 'Madhu14777';
ERROR:  syntax error at or near "psql"
LINE 1: psql -U postgres
        ^
postgres=# ALTER ROLE madhu WITH LOGIN PASSWORD 'Madhu14777';
ALTER ROLE
postgres=# psql -U madhu -d university_db
postgres-# GRANT ALL PRIVILEGES ON DATABASE university_db TO madhu;
ERROR:  syntax error at or near "psql"
LINE 1: psql -U madhu -d university_db
        ^
postgres=# GRANT ALL PRIVILEGES ON DATABASE university_db TO madhu;
GRANT
postgres=# \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db;
Password for user madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  database "university_db;" does not exist

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db;
Password for user madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  database "university_db;" does not exist

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> CREATE TABLE students(first_name VARCHAR(50),last_name VARCHAR(50),student_id INTEGER, email VARCHAR(100),date_of_birth DATE);
CREATE TABLE
university_db=> \d
         List of relations
 Schema |   Name   | Type  | Owner
--------+----------+-------+-------
 public | students | table | madhu
(1 row)


university_db=> \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U university_db
Password for user university_db:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "university_db"

C:\Users\Minfy.CHILUKURIVASUSR>postgres -U university_db
illegal option -- U
Try "postgres --help" for more information.

C:\Users\Minfy.CHILUKURIVASUSR>psql -U Madhu -d university_db
Password for user Madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Madhu"

C:\Users\Minfy.CHILUKURIVASUSR>psql -U Madhu -d university_db
Password for user Madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Madhu"

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> \\dt
invalid command \
Try \? for help.
university_db=> \dt
         List of relations
 Schema |   Name   | Type  | Owner
--------+----------+-------+-------
 public | students | table | madhu
(1 row)


university_db=> ALTER TABLE students ADD COLUMN enrollment_date DATE;
ALTER TABLE
university_db=> ALTER TABLE students DROP enrollment_date;
ALTER TABLE
university_db=> ALTER TABLE students ADD COLUMN enrollment_date DATE;
ALTER TABLE
university_db=> ALTER TABLE students DROP enrollment_date;
ALTER TABLE
university_db=>
university_db=>
university_db=> ALTER TABLE students ALTER COLUMN email TYPE VARCHAR(120);
ALTER TABLE
university_db=> ALTER TABLE students ALTER RENAME COLUMN date_of_birth TO dob;
ERROR:  syntax error at or near "COLUMN"
LINE 1: ALTER TABLE students ALTER RENAME COLUMN date_of_birth TO do...
                                          ^
university_db=> ALTER TABLE students ALTER RENAME COLUMN date_of_birth TO dob;
ERROR:  syntax error at or near "COLUMN"
LINE 1: ALTER TABLE students ALTER RENAME COLUMN date_of_birth TO do...
                                          ^
university_db=> ALTER TABLE students ALTER RENAME COLUMN date_of_birth TO dob;
ERROR:  syntax error at or near "COLUMN"
LINE 1: ALTER TABLE students ALTER RENAME COLUMN date_of_birth TO do...
                                          ^
university_db=> ALTER TABLE students RENAME COLUMN date_of_birth TO dob;
ALTER TABLE
university_db=> ALTER TABLE students ADD CONSTRAINT unique_emai
university_db-> ALTER TABLE students ADD CONSTRAINT unique_emailUNIQUE(email)
university_db-> ALTER TABLE students ADD CONSTRAINT unique_emailUNIQUE(email)
university_db-> ALTER TABLE students ADD CONSTRAINT unique_email UNIQUE(email)
university_db-> ALTER TABLE students ADD COLUMN phone_number TYPE VARCHAR(20);
ERROR:  syntax error at or near "ALTER"
LINE 2: ALTER TABLE students ADD CONSTRAINT unique_emailUNIQUE(email...
        ^
university_db=> ALTER TABLE students ADD COLUMN phone_number TYPE VARCHAR(20);
ERROR:  syntax error at or near "VARCHAR"
LINE 1: ALTER TABLE students ADD COLUMN phone_number TYPE VARCHAR(20...
                                                          ^
university_db=> ALTER TABLE students ADD COLUMN phone_number TYPE VARCHAR(20);
ERROR:  syntax error at or near "VARCHAR"
LINE 1: ALTER TABLE students ADD COLUMN phone_number TYPE VARCHAR(20...
                                                          ^
university_db=> ALTER TABLE students ADD COLUMN phone_number VARCHAR(20);
ALTER TABLE
university_db=> ALTER TABLE students DROP COLUMN phone_number
university_db-> ALTER TABLE students DROP COLUMN phone_number;
ERROR:  syntax error at or near "ALTER"
LINE 2: ALTER TABLE students DROP COLUMN phone_number;
        ^
university_db=> ALTER TABLE students DROP COLUMN phone_number;
ALTER TABLE
university_db=> INSERT INTO students (student_id,first_name,last_name,email,dob)
university_db-> VALUES (1,'MADHU','KUMAR','example@gmail.com',10-01-2992)
university_db-> VALUES(2,'HARSHA','VERSE','kiunh@gmail.com',2-3-4)
university_db-> VALUES(4,'MAHESH','KHALEJA','maheshbabhu@gmail.com',3-4-5)
university_db-> VALUES(3,'PRABHAS','SAAHO','prabhas@gmail.com)
university_db'> VALUES(5,'PAWAN','HHVM','pawan@gmail.com);
ERROR:  syntax error at or near "VALUES"
LINE 3: VALUES(2,'HARSHA','VERSE','kiunh@gmail.com',2-3-4)
        ^
university_db=> VALUES(2,'HARSHA','VERSE','kiunh@gmail.com',2-3-4);
 column1 | column2 | column3 |     column4     | column5
---------+---------+---------+-----------------+---------
       2 | HARSHA  | VERSE   | kiunh@gmail.com |      -5
(1 row)


university_db=> VALUES (1,'MADHU','KUMAR','example@gmail.com',10-01-2992)
university_db-> INSERT INTO students (student_id,first_name,last_name,email,dob)
university_db-> VALUES(2,'HAR
university_db'>
university_db'>
university_db'> ;
university_db'> MA
university_db'> /q
university_db'> \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U  madhu -d university_admin
Password for user madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  database "university_admin" does not exist

C:\Users\Minfy.CHILUKURIVASUSR>psql -U  madhu -d university_admin
Password for user madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  database "university_admin" does not exist

C:\Users\Minfy.CHILUKURIVASUSR>psql -U  madhu -d university_admin;
Password for user madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  database "university_admin;" does not exist

C:\Users\Minfy.CHILUKURIVASUSR>psql -U  madhu -d university_admin
Password for user madhu:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "madhu"

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> INSERT INTO students (student_id,first_name,last_name,dob)
university_db-> VALUES(1,'MADHU','KUMAR','10-01-2002'),
university_db-> VALUES(2,'MAHESH','BABU','12-2-2001');
ERROR:  syntax error at or near "VALUES"
LINE 3: VALUES(2,'MAHESH','BABU','12-2-2001');
        ^
university_db=> INSERT INTO students (student_id,first_name,last_name,dob)
university_db-> VALUES
university_db-> (1,'MADHU','KUMAR','10-01-2002'),002'),
university_db'> (1,'MADHU','KUMAR','10-01-2002'),002'),
university_db-> (1,'MADHU','KUMAR','10-01-2002'),002');
university_db'> \q
Use control-C to quit.
university_db'> \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> INSERT INTO students (student_id,first_name,last_name,dob,email)
university_db-> VALUES
university_db-> (1,'MADHU','KUMAR','10-01-2002','madddy@gmail.com),
university_db'> (2,'MAHESH','BABU','2-3-4','mahi@gmail.com);
ERROR:  syntax error at or near "MAHESH"
LINE 4: (2,'MAHESH','BABU','2-3-4','mahi@gmail.com);
            ^
university_db=> INSERT INTO students (student_id,first_name,last_name,dob,email)
university_db-> VALUES
university_db-> (1,'MADHU','KUMAR','2002-01-10','madhukumar@gmail.com'),(2,'Harsha','Kumar','2005-12-3,'john@gmail.com'),(3,'qwert','yuiop','1002-01-20','qwerty@gmail.com'),(4,'asdf','ghjk','2001-06-11','asdfg@gmail.com'),(5,'zxcvb','vbnm','1998-02-22','zxcvb@gmail.com');
university_db'> SELECT * FROM students;
university_db'> \q
Use control-C to quit.
university_db'> \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> SELECT * FROM students;
 first_name | last_name | student_id | email | dob
------------+-----------+------------+-------+-----
(0 rows)


university_db=> INSERT INTO students (student_id,first_name,last_name,dob,email)
university_db-> VALUES (1,'MADHU','KUMAR','2002-01-10','madhukumar@gmail.com'),(2,'Harsha','Kumar','2005-12-3,'john@gmail.com'),(3,'qwert','yuiop','1002-01-20','qwerty@gmail.com'),(4,'asdf','ghjk','2001-06-11','asdfg@gmail.com'),(5,'zxcvb','vbnm','1998-02-22','zxcvb@gmail.com');
university_db'> select * from students
university_db'> ;
university_db'> select * from students;
university_db'> \q
Use control-C to quit.
university_db'> \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> INSERT INTO students (student_id,first_name,last_name,dob,email)
university_db-> VALUES (1,'MADHU','KUMAR','2002-01-10','madhukumar@gmail.com'),(2,'Harsha','Kumar','2005-12-3,'john@gmail.com'),(3,'qwert','yuiop','1002-01-20','qwerty@gmail.com'),(4,'asdf','ghjk','2001-06-11','asdfg@gmail.com'),(5,'zxcvb','vbnm','1998-02-22','zxcvb@gmail.com');
university_db'> VALUES (1,'MADHU','KUMAR','2002-01-10','madhukumar@gmail.com'),(2,'Harsha','Kumar','2005-12-3,'john@gmail.com'),(3,'qwert','yuiop','1994-01-20','qwerty@gmail.com'),(4,'asdf','ghjk','2001-06-11','asdfg@gmail.com'),(5,'zxcvb','vbnm','1998-02-22','zxcvb@gmail.com');
ERROR:  syntax error at or near "john"
LINE 2: ...kumar@gmail.com'),(2,'Harsha','Kumar','2005-12-3,'john@gmail...
                                                             ^
university_db=> INSERT INTO students (student_id,first_name,last_name,dob,email)
university_db-> VALUES (1,'MADHU','KUMAR','2002-01-10','madhukumar@gmail.com'),(2,'Harsha','Kumar','2005-12-3,'john@gmail.com'),(3,'qwert','yuiop','1994-01-20','qwerty@gmail.com'),(4,'asdf','ghjk','2001-06-11','asdfg@gmail.com'),(5,'zxcvb','vbnm','1998-02-22','zxcvb@gmail.com');
university_db'> select 8 from students;
university_db'> select * from students;
university_db'>
university_db'>
university_db'>
university_db'>
university_db'>
university_db'>
university_db'>
university_db'>
university_db'> \q
Use control-C to quit.
university_db'> \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> select * from students;
 first_name | last_name | student_id | email | dob
------------+-----------+------------+-------+-----
(0 rows)


university_db=> INSERT INTO students (student_id,first_name,last_name,dob,email)
university_db-> VALUES (1,'MADHU','KUMAR','2002-01-10','madhukumar@gmail.com'),(2,'Harsha','Kumar','2005-12-3,'john@gmail.com'),(3,'qwert','yuiop','1994-01-20','qwerty@gmail.com'),(4,'asdf','ghjk','2001-06-11','asdfg@gmail.com'),(5,'zxcvb','vbnm','1998-02-22','zxcvb@gmail.com');
university_db'> INSERT INTO students (student_id, first_name, last_name, dob, email)
university_db'> VALUES
university_db'>   (1, 'MADHU', 'KUMAR', '2002-01-10', 'madhukumar@gmail.com'),
university_db'>   (2, 'Harsha', 'Kumar', '2005-12-03', 'john@gmail.com'),
university_db'>   (3, 'qwert', 'yuiop', '1994-01-20', 'qwerty@gmail.com'),
university_db'>   (4, 'asdf', 'ghjk', '2001-06-11', 'asdfg@gmail.com'),
university_db'>   (5, 'zxcvb', 'vbnm', '1998-02-22', 'zxcvb@gmail.com');
university_db'>
university_db'> \q
Use control-C to quit.
university_db'> \q

C:\Users\Minfy.CHILUKURIVASUSR>psql -U madhu -d university_db
Password for user madhu:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> INSERT INTO students (student_id, first_name, last_name, dob, email)
university_db-> VALUES
university_db->   (1, 'MADHU', 'KUMAR', '2002-01-10', 'madhukumar@gmail.com'),
university_db->   (2, 'Harsha', 'Kumar', '2005-12-03', 'john@gmail.com'),
university_db->   (3, 'qwert', 'yuiop', '1994-01-20', 'qwerty@gmail.com'),
university_db->   (4, 'asdf', 'ghjk', '2001-06-11', 'asdfg@gmail.com'),
university_db->   (5, 'zxcvb', 'vbnm', '1998-02-22', 'zxcvb@gmail.com');
INSERT 0 5
university_db=> select * from students;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 2005-12-03
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
(5 rows)


university_db=> select * from students where student_id=1
university_db-> select * from students where student_id=1;
ERROR:  syntax error at or near "select"
LINE 2: select * from students where student_id=1;
        ^
university_db=> select * from students where student_id=1;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
(1 row)


university_db=> select * from students where dob>='02-01-1990'
university_db-> ;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 2005-12-03
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
(5 rows)


university_db=> select * from students where dob>='02-01-2000';
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 2005-12-03
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
(3 rows)


university_db=> select * from students where firstname like '%A';
ERROR:  column "firstname" does not exist
LINE 1: select * from students where firstname like '%A';
                                     ^
HINT:  Perhaps you meant to reference the column "students.first_name".
university_db=> select * from students where first_name like '%A';
 first_name | last_name | student_id | email | dob
------------+-----------+------------+-------+-----
(0 rows)


university_db=> select * from students where first_name like 'A%';
 first_name | last_name | student_id | email | dob
------------+-----------+------------+-------+-----
(0 rows)


university_db=> select * from student where student_id=1 or student_id=3;
ERROR:  relation "student" does not exist
LINE 1: select * from student where student_id=1 or student_id=3;
                      ^
university_db=> select * from students where student_id=1 or student_id=3;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
(2 rows)


university_db=> select * from students where student_id in (1,5);
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
(2 rows)


university_db=> INSERT INTO student(student_id,first_name,last_name,email,dob) VALUES (6,'Shaky','M',,'10-02-1002');
ERROR:  syntax error at or near ","
LINE 1: ...t_name,last_name,email,dob) VALUES (6,'Shaky','M',,'10-02-10...
                                                             ^
university_db=> INSERT INTO student(student_id,first_name,last_name,email,dob) VALUES (6,'Shaky','M',"",'10-02-1002');
ERROR:  zero-length delimited identifier at or near """"
LINE 1: ...t_name,last_name,email,dob) VALUES (6,'Shaky','M',"",'10-02-...
                                                             ^
university_db=> INSERT INTO student(student_id,first_name,last_name,dob) VALUES (6,'Shaky','M','10-02-1002');
ERROR:  relation "student" does not exist
LINE 1: INSERT INTO student(student_id,first_name,last_name,dob) VAL...
                    ^
university_db=> INSERT INTO students (student_id,first_name,last_name,dob) VALUES (6,'Shaky','M','10-02-1002');
INSERT 0 1
university_db=> select * from students where email is null;
 first_name | last_name | student_id | email |    dob
------------+-----------+------------+-------+------------
 Shaky      | M         |          6 |       | 1002-10-02
(1 row)


university_db=> select * from students where email is not null;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 2005-12-03
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
(5 rows)


university_db=> select * from students where dob>'10-01-2003';
 first_name | last_name | student_id |     email      |    dob
------------+-----------+------------+----------------+------------
 Harsha     | Kumar     |          2 | john@gmail.com | 2005-12-03
(1 row)


university_db=> select * from students where first_name like 'A%' or first_name like '%B';
 first_name | last_name | student_id | email | dob
------------+-----------+------------+-------+-----
(0 rows)


university_db=> select * from students where first_name like 'M%' or first_name like '%y';
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Shaky      | M         |          6 |                      | 1002-10-02
(2 rows)


university_db=> UPDATE students
university_db-> set dob='1992-09-10' where student_id=2;
UPDATE 1
university_db=> select * from students;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 Shaky      | M         |          6 |                      | 1002-10-02
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
(6 rows)


university_db=> Update students
university_db-> set email="polaki@gmail.com" where student_id=6;
ERROR:  column "polaki@gmail.com" does not exist
LINE 2: set email="polaki@gmail.com" where student_id=6;
                  ^
university_db=> set email='polaki@gmail.com' where student_id=6;
ERROR:  syntax error at or near "where"
LINE 1: set email='polaki@gmail.com' where student_id=6;
                                     ^
university_db=> set email='polaki@gmail.com' where student_id=6;
ERROR:  syntax error at or near "where"
LINE 1: set email='polaki@gmail.com' where student_id=6;
                                     ^
university_db=> Update students
university_db-> set email='polaki@gmail.com' where student_id=6;
UPDATE 1
university_db=> SELECT * from students ORDER BY last_name by DESC;
ERROR:  syntax error at or near "by"
LINE 1: SELECT * from students ORDER BY last_name by DESC;
                                                  ^
university_db=> SELECT * from students ORDER BY last_name DESC;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
(6 rows)


university_db=> SELECT * from students ORDER BY last_name ASC;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
(6 rows)


university_db=> SELECT * from students ORDER BY last_name by ASC;
ERROR:  syntax error at or near "by"
LINE 1: SELECT * from students ORDER BY last_name by ASC;
                                                  ^
university_db=> SELECT * from students ORDER BY last_name ASC;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
(6 rows)


university_db=> SELECT * from students ORDER BY last_name ,first_name;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
(6 rows)


university_db=> SELECT * from students ORDER BY last_name DESC;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
(6 rows)


university_db=> SELECT * from students ORDER BY last_name ,first_name;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
(6 rows)


university_db=> select * from students order by dob DESC;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
(6 rows)


university_db=> select * from students order by dob ;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
(6 rows)


university_db=> select * from students order by last_name desc and order by first_name asc;
ERROR:  syntax error at or near "and"
LINE 1: select * from students order by last_name desc and order by ...
                                                       ^
university_db=> select * from students order by last_name desc,first_name asc;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
(6 rows)


university_db=> select * from students order by last_name desc,first_name asc;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
(6 rows)


university_db=> select * from students order by dob desc limit 2;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
(2 rows)


university_db=> select * from students order by dob desc limit 2 offst 2;
ERROR:  syntax error at or near "offst"
LINE 1: select * from students order by dob desc limit 2 offst 2;
                                                         ^
university_db=> select * from students order by dob desc limit 2 offset 2;
 first_name | last_name | student_id |      email       |    dob
------------+-----------+------------+------------------+------------
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com  | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com | 1994-01-20
(2 rows)


university_db=> select * from students order by dob limit 2;
 first_name | last_name | student_id |      email       |    dob
------------+-----------+------------+------------------+------------
 Shaky      | M         |          6 | polaki@gmail.com | 1002-10-02
 Harsha     | Kumar     |          2 | john@gmail.com   | 1992-09-10
(2 rows)


university_db=> select * from students order by student_id limit 2 offset 1;
 first_name | last_name | student_id |      email       |    dob
------------+-----------+------------+------------------+------------
 Harsha     | Kumar     |          2 | john@gmail.com   | 1992-09-10
 qwert      | yuiop     |          3 | qwerty@gmail.com | 1994-01-20
(2 rows)


university_db=> INSERT INTO students(student_id,first_name,last_name,dob,email) VALUES (7,'HARSHITH','RONA','1922-02-14','harshith@gmail.com');
INSERT 0 1
university_db=> SELECT DISTINCT last_name from students;
 last_name
-----------
 RONA
 yuiop
 vbnm
 M
 Kumar
 KUMAR
 ghjk
(7 rows)


university_db=> select DISTINCT * from students;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 HARSHITH   | RONA      |          7 | harshith@gmail.com   | 1922-02-14
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
(7 rows)


university_db=> INSERT INTO students (student_id,email,first_name,last_name,dob) VALUES(8,'qwerty@gmail.com','Shaky','Kumar','1998-02-22');
INSERT 0 1
university_db=> select DISTINCT * from students;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 asdf       | ghjk      |          4 | asdfg@gmail.com      | 2001-06-11
 Shaky      | Kumar     |          8 | qwerty@gmail.com     | 1998-02-22
 HARSHITH   | RONA      |          7 | harshith@gmail.com   | 1922-02-14
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
(8 rows)


university_db=> select COUNT(*) from students AS total_students;
 count
-------
     8
(1 row)


university_db=> select COUNT(*) from students where email is not null;
 count
-------
     8
(1 row)


university_db=> select COUNT(*) from students where email is null;
 count
-------
     0
(1 row)


university_db=> update students
university_db-> set email=null where student_id=4;
UPDATE 1
university_db=> select COUNT(*) from students where email is null;
 count
-------
     1
(1 row)


university_db=> select COUNT(*) from students where email is not null;
 count
-------
     7
(1 row)


university_db=> select COUNT(*) from students where DISTINCT last_name;
ERROR:  syntax error at or near "DISTINCT"
LINE 1: select COUNT(*) from students where DISTINCT last_name;
                                            ^
university_db=> select COUNT(*) from students where distinct last_name;
ERROR:  syntax error at or near "distinct"
LINE 1: select COUNT(*) from students where distinct last_name;
                                            ^
university_db=> select distinct last_name from students;
 last_name
-----------
 RONA
 yuiop
 vbnm
 M
 Kumar
 KUMAR
 ghjk
(7 rows)


university_db=> select COUNT(*) distinct last_name from students;
ERROR:  syntax error at or near "last_name"
LINE 1: select COUNT(*) distinct last_name from students;
                                 ^
university_db=> select COUNT(*) distinct last_name from students;
ERROR:  syntax error at or near "last_name"
LINE 1: select COUNT(*) distinct last_name from students;
                                 ^
university_db=> select COUNT(distinct last_name) from students;
 count
-------
     7
(1 row)


university_db=> select last_name,COUNT(*) AS number_of_students
university_db-> FROM students
university_db-> OREDER BY last_name
university_db-> ORDER BY number_of_students DESC;
ERROR:  syntax error at or near "BY"
LINE 3: OREDER BY last_name
               ^
university_db=> select last_name,COUNT(*) AS number_of_students
university_db-> FROM students
university_db-> OREDER BY last_name
university_db-> ORDER BY number_of_students DESC;
ERROR:  syntax error at or near "BY"
LINE 3: OREDER BY last_name
               ^
university_db=> select last_name,COUNT(*) AS number_of_students
university_db-> FROM students
university_db-> ORDER BY last_name
university_db-> ORDER BY number_of_students DESC;
ERROR:  syntax error at or near "ORDER"
LINE 4: ORDER BY number_of_students DESC;
        ^
university_db=> select last_name,COUNT(*) AS number_of_students
university_db-> FROM students
university_db-> ORDER BY last_name
university_db-> ;
ERROR:  column "students.last_name" must appear in the GROUP BY clause or be used in an aggregate function
LINE 1: select last_name,COUNT(*) AS number_of_students
               ^
university_db=> select last_name,COUNT(*) AS number_of_students
university_db-> FROM students
university_db-> ORDER BY last_namee
university_db-> ;
ERROR:  column "last_namee" does not exist
LINE 3: ORDER BY last_namee
                 ^
HINT:  Perhaps you meant to reference the column "students.last_name".
university_db=> select last_name,COUNT(*) AS number_of_students
university_db-> FROM students
university_db-> GROUP BY last_name;
 last_name | number_of_students
-----------+--------------------
 RONA      |                  1
 yuiop     |                  1
 vbnm      |                  1
 M         |                  1
 Kumar     |                  2
 KUMAR     |                  1
 ghjk      |                  1
(7 rows)


university_db=> select * from students
university_db-> ;
 first_name | last_name | student_id |        email         |    dob
------------+-----------+------------+----------------------+------------
 MADHU      | KUMAR     |          1 | madhukumar@gmail.com | 2002-01-10
 qwert      | yuiop     |          3 | qwerty@gmail.com     | 1994-01-20
 zxcvb      | vbnm      |          5 | zxcvb@gmail.com      | 1998-02-22
 Harsha     | Kumar     |          2 | john@gmail.com       | 1992-09-10
 Shaky      | M         |          6 | polaki@gmail.com     | 1002-10-02
 HARSHITH   | RONA      |          7 | harshith@gmail.com   | 1922-02-14
 Shaky      | Kumar     |          8 | qwerty@gmail.com     | 1998-02-22
 asdf       | ghjk      |          4 |                      | 2001-06-11
(8 rows)


university_db=> select COUNT(distinct first_name) from students;
 count
-------
     7
(1 row)


university_db=> select dob,COUNT(*) AS number_of_student born in each_year
university_db-> from students
university_db-> GROUP BY dob;
ERROR:  syntax error at or near "born"
LINE 1: select dob,COUNT(*) AS number_of_student born in each_year
                                                 ^
university_db=> select dob,COUNT(*) AS number_of_student_bornin_each_yearr
university_db-> from students
university_db-> GROUP BY dob;
    dob     | number_of_student_bornin_each_yearr
------------+-------------------------------------
 1992-09-10 |                                   1
 2001-06-11 |                                   1
 1922-02-14 |                                   1
 1994-01-20 |                                   1
 1998-02-22 |                                   2
 2002-01-10 |                                   1
 1002-10-02 |                                   1
(7 rows)


university_db=> select extract(year from dob),COUNT(*) AS number_of_student born in each_year
university_db-> from students
university_db-> GROUP BY dob;
ERROR:  syntax error at or near "born"
LINE 1: ...ract(year from dob),COUNT(*) AS number_of_student born in ea...
                                                             ^
university_db=> select dob,COUNT(*) AS number_of_student_bornin_each_yearr
university_db-> from students
university_db-> GROUP BY dob;
    dob     | number_of_student_bornin_each_yearr
------------+-------------------------------------
 1992-09-10 |                                   1
 2001-06-11 |                                   1
 1922-02-14 |                                   1
 1994-01-20 |                                   1
 1998-02-22 |                                   2
 2002-01-10 |                                   1
 1002-10-02 |                                   1
(7 rows)


university_db=> select extract(year from dob),COUNT(*) AS number_of_student born in each_year
university_db-> ;
ERROR:  syntax error at or near "born"
LINE 1: ...ract(year from dob),COUNT(*) AS number_of_student born in ea...
                                                             ^
university_db=> select extract(year from dob),COUNT(*) AS number_of_student_bornin_each_year
university_db-> from students
university_db-> GROUP BY dob;
 extract | number_of_student_bornin_each_year
---------+------------------------------------
    1992 |                                  1
    2001 |                                  1
    1922 |                                  1
    1994 |                                  1
    1998 |                                  2
    2002 |                                  1
    1002 |                                  1
(7 rows)


university_db=> select extract(year from dob) AS year,COUNT(*) AS number_of_student born in each_year
university_db-> from students
university_db-> ;
ERROR:  syntax error at or near "born"
LINE 1: ...r from dob) AS year,COUNT(*) AS number_of_student born in ea...
                                                             ^
university_db=> select extract(year from dob) AS year,COUNT(*) AS number_of_student_bornin_each_year
university_db-> from students
university_db-> GROUP BY dob;
 year | number_of_student_bornin_each_year
------+------------------------------------
 1992 |                                  1
 2001 |                                  1
 1922 |                                  1
 1994 |                                  1
 1998 |                                  2
 2002 |                                  1
 1002 |                                  1
(7 rows)


university_db=> select extract(year from dob) AS year,COUNT(*) AS number_of_student_bornin_each_year
university_db-> from students
university_db-> GROUP BY year;
 year | number_of_student_bornin_each_year
------+------------------------------------
 1002 |                                  1
 1998 |                                  2
 1994 |                                  1
 1992 |                                  1
 1922 |                                  1
 2002 |                                  1
 2001 |                                  1
(7 rows)


university_db=> DROP students;
ERROR:  syntax error at or near "students"
LINE 1: DROP students;
             ^
university_db=> DROP students;
ERROR:  syntax error at or near "students"
LINE 1: DROP students;
             ^
university_db=> DROP TABLE students;
DROP TABLE
university_db=> CREATE STUDENTS(
university_db(> student_id INTEGER NOT NULL;
university_db(> first_name VARCHAR(50) NOT NULL;
university_db(> last_name VARCHAR(50) NOT NULL:
university_db(> dob DATE;
university_db(> email VARCHAR(50) NOT NULL;
university_db(> enrollment_status VARCHAR(10) CHECK (enrollment_status in('enrolled','graduated','dropped')
university_db(> );
university_db(> ));
ERROR:  syntax error at or near "STUDENTS"
LINE 1: CREATE STUDENTS(
               ^
university_db=> CREATE STUDENTS(
university_db(> student_id INTEGER NOT NULL;
university_db(> first_name VARCHAR(50) NOT NULL;
university_db(> last_name VARCHAR(50) NOT NULL:
university_db(> dob DATE;
university_db(> email VARCHAR(50) NOT NULL;
university_db(> enrollment_status VARCHAR(10) CHECK (enrollment_status in('enrolled','graduated','dropped')
university_db(> ));
ERROR:  syntax error at or near "STUDENTS"
LINE 1: CREATE STUDENTS(
               ^
university_db=> CREATE TABLE STUDENTS(
university_db(> student_id INTEGER NOT NULL;
university_db(> first_name VARCHAR(50) NOT NULL;
university_db(> last_name VARCHAR(50) NOT NULL:
university_db(> dob DATE;
university_db(> email VARCHAR(50) NOT NULL;
university_db(> enrollment_status VARCHAR(10) CHECK (enrollment_status in('enrolled','graduated','dropped')
university_db(> ));
ERROR:  syntax error at or near ";"
LINE 2: student_id INTEGER NOT NULL;
                                   ^
university_db=> CREATE TABLE STUDENTS(
university_db(> student_id INTEGER NOT NULL,
university_db(> first_name VARCHAR(50) NOT NULL,
university_db(> last_name VARCHAR(50) NOT NULL,
university_db(> dob DATE,
university_db(> email VARCHAR(50) NOT NULL,
university_db(> enrollment_status VARCHAR(10) CHECK (enrollment_status in('enrolled','graduated','dropped')
university_db(> ));
CREATE TABLE
university_db=> update students
university_db-> set email UNIQUE;
ERROR:  syntax error at or near "UNIQUE"
LINE 2: set email UNIQUE;
                  ^
university_db=> ALTER TABLE students
university_db-> ADD CONSTRAINT unique_email UNIQUE (email);
ALTER TABLE
university_db=> ALTER TABLE students
university_db-> REMOVE CONSTRAINT email;
ERROR:  syntax error at or near "REMOVE"
LINE 2: REMOVE CONSTRAINT email;
        ^
university_db=> ALTER TABLE students
university_db-> DROP CONSTRAINT email;
ERROR:  constraint "email" of relation "students" does not exist
university_db=> ALTER TABLE students
university_db-> DROP CONSTRAINT unique_email;
ALTER TABLE
university_db=> ALTER TABLE students
university_db-> ADD CONSTRAINT unique_email UNIQUE (email);
ALTER TABLE
university_db=> ALTER TABLE students
university_db-> ALTER COLUMN email DROP NOT NULL;
ALTER TABLE
university_db=> \d students
                          Table "public.students"
      Column       |         Type          | Collation | Nullable | Default
-------------------+-----------------------+-----------+----------+---------
 student_id        | integer               |           | not null |
 first_name        | character varying(50) |           | not null |
 last_name         | character varying(50) |           | not null |
 dob               | date                  |           |          |
 email             | character varying(50) |           |          |
 enrollment_status | character varying(10) |           |          |
Indexes:
    "unique_email" UNIQUE CONSTRAINT, btree (email)
Check constraints:
    "students_enrollment_status_check" CHECK (enrollment_status::text = ANY (ARRAY['enrolled'::character varying, 'graduated'::character varying, 'dropped'::character varying]::text[]))


university_db=> DROP TABLE students;
DROP TABLE
university_db=>
university_db=> CREATE TABLE students (
university_db(>     student_id SERIAL PRIMARY KEY,  -- student_id is now PK, auto-incrementing, NOT NULL
university_db(>     first_name VARCHAR(50) NOT NULL,
university_db(>     last_name VARCHAR(50) NOT NULL,
university_db(>     email VARCHAR(100) UNIQUE,      -- Email should be unique; can be NULL unless NOT NULL is added
university_db(>     dob DATE,
university_db(>     enrollment_status VARCHAR(20) CHECK (enrollment_status IN ('enrolled', 'graduated', 'dropped', 'pending'))
university_db(> );
CREATE TABLE
university_db=> /d students
university_db-> \d students
                                             Table "public.students"
      Column       |          Type          | Collation | Nullable |                   Default
-------------------+------------------------+-----------+----------+----------------------------------------------
 student_id        | integer                |           | not null | nextval('students_student_id_seq'::regclass)
 first_name        | character varying(50)  |           | not null |  last_name         | character varying(50)  |           | not null |  email             | character varying(100) |           |          |  dob               | date                   |           |          |  enrollment_status | character varying(20)  |           |          | Indexes:
    "students_pkey" PRIMARY KEY, btree (student_id)
    "students_email_key" UNIQUE CONSTRAINT, btree (email)
Check constraints:
    "students_enrollment_status_check" CHECK (enrollment_status::text = ANY (ARRAY['enrolled'::character varying, 'graduated'::character varying, 'dropped'::character varying, 'pending'::character varying]::text[]))


university_db-> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Alice', 'Smith', 'alice.smith@example.com', '2003-05-15', 'enrolled');
ERROR:  syntax error at or near "/"
LINE 1: /d students
        ^
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Robert', 'Johnson', 'robert.j@example.com', '2002-08-22', 'enrolled');
INSERT 0 1
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Charlie', 'Brown', 'charlie.brown@example.com', '2003-01-10', 'pending');
INSERT 0 1
university_db=> select * from students;
 student_id | first_name | last_name |           email           |    dob     | enrollment_status
------------+------------+-----------+---------------------------+------------+-------------------
          1 | Robert     | Johnson   | robert.j@example.com      | 2002-08-22 | enrolled
          2 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10 | pending
(2 rows)


university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Robert', 'Johnson', 'robert.j@example.com', '2002-08-22', 'pusky');
ERROR:  new row for relation "students" violates check constraint "students_enrollment_status_check"
DETAIL:  Failing row contains (3, Robert, Johnson, robert.j@example.com, 2002-08-22, pusky).
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Robert', 'Jonny', 'robert.j@example.com', '2002-08-22', 'pending');
ERROR:  duplicate key value violates unique constraint "students_email_key"
DETAIL:  Key (email)=(robert.j@example.com) already exists.
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Robert', 'Jonny', 'robert.k@example.com', '2002-08-22', 'pending');
INSERT 0 1
university_db=> select * from students;
 student_id | first_name | last_name |           email           |    dob     | enrollment_status
------------+------------+-----------+---------------------------+------------+-------------------
          1 | Robert     | Johnson   | robert.j@example.com      | 2002-08-22 | enrolled
          2 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10 | pending
          5 | Robert     | Jonny     | robert.k@example.com      | 2002-08-22 | pending
(3 rows)


university_db=> CREATE TABLE courses(
university_db(> course_id SERIAL PRIMARY KEY,
university_db(> course_name VARCHAR(30) NOT NULL UNIQUE,
university_db(> credits INTEGER check(credits>0 AND credits<10)
university_db(> );
CREATE TABLE
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Introduction to SQL', 3);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Database Design', 4);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Web Development', 3);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Data Structures', 4);
INSERT 0 1
university_db=> create table enrollments(
university_db(> enrollment_id SERIAL primary key,
university_db(> student_id integer not null,
university_db(> course_id integer not null,
university_db(> enrollment_date DATE DEFAULT CURRENT_DATE,
university_db(>  grade CHAR(1) CHECK (grade IN ('A', 'B', 'C', 'D', 'F', 'W', NULL)),
university_db(> CONSTRAINT fk_student FOREIGN KEY (student_id) REFERENCES students(student_id)
university_db(> ON DELETE CASCADE,
university_db(> CONSTRAINT fk_course
university_db(>         FOREIGN KEY (course_id)
university_db(>         REFERENCES courses(course_id)
university_db(>         ON DELETE RESTRICT,
university_db(> UNIQUE (student_id, course_id)
university_db(> );
CREATE TABLE
university_db=> INSERT INTO enrollments (student_id, course_id, grade) VALUES (1, 1, 'A');
INSERT 0 1
university_db=> INSERT INTO enrollments (student_id, course_id) VALUES (1, 2);
INSERT 0 1
university_db=> INSERT INTO enrollments (student_id, course_id, grade) VALUES (2, 1, 'B');
INSERT 0 1
university_db=>
university_db=>
university_db=> select * from enrollments
university_db-> ;
 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
             1 |          1 |         1 | 2025-05-30      | A
             2 |          1 |         2 | 2025-05-30      |
             3 |          2 |         1 | 2025-05-30      | B
(3 rows)


university_db=> select * from courses;
 course_id |     course_name     | credits
-----------+---------------------+---------
         1 | Introduction to SQL |       3
         2 | Database Design     |       4
         3 | Web Development     |       3
         4 | Data Structures     |       4
(4 rows)


university_db=> SELECT * FROM students WHERE student_id = 1;SELECT * FROM enrollments WHERE student_id = 1;DELETE FROM students WHERE student_id = 1; -- Alice
 student_id | first_name | last_name |        email         |    dob     | enrollment_status
------------+------------+-----------+----------------------+------------+-------------------
          1 | Robert     | Johnson   | robert.j@example.com | 2002-08-22 | enrolled
(1 row)


 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
             1 |          1 |         1 | 2025-05-30      | A
             2 |          1 |         2 | 2025-05-30      |
(2 rows)


DELETE 1
university_db=> SELECT * FROM students WHERE student_id = 1; -- Should be gone
 student_id | first_name | last_name | email | dob | enrollment_status
------------+------------+-----------+-------+-----+-------------------
(0 rows)
