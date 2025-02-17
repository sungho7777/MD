# MySQL
## 명령어
+ MySQL root 접속
    ```cmd
    PS C:\Users\mzncv> mysql -u root -p
    Enter password: ****
    ```

+ DATABASE 생성
    ```mysql
    mysql> CREATE DATABASE TESTDB;
    Query OK, 1 row affected (0.02 sec)
    ```

+ DATABASE 제거
    ```mysql
    mysql> DROP DATABASE TESTDB;  
    Query OK, 0 rows affected (0.03 sec)
    ```

+ DATABASE 목록 조회
    ```mysql
    mysql> SHOW DATABASES;
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | testdb             |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

+ DATABASE 사용하기
    ```mysql
    mysql> USE TESTDB;
    Database changed
    ```

+ 현재 사용중인 DATABASE 조회하기기 
    ```mysql
    mysql> select DATABASE();
    +------------+
    | DATABASE() |
    +------------+
    | testdb     |
    +------------+
    1 row in set (0.00 sec)
    ```

+ 사용자 조회
    ```mysql
    USE MYSQL;
    SELECT HOST, USER FROM USER;
    ```

+ 사용자 생성
    ```mysql
    mysql> CREATE USER 'TESTUSER1'@'LOCALHOST' IDENTIFIED BY '1234';
    Query OK, 0 rows affected (0.02 sec)

    mysql> CREATE USER 'TESTUSER2'@'LOCALHOST' IDENTIFIED BY '1234';
    Query OK, 0 rows affected (0.01 sec)

    mysql> CREATE USER 'TESTUSER3'@'LOCALHOST' IDENTIFIED BY '1234';
    Query OK, 0 rows affected (0.02 sec)

    mysql> CREATE USER 'TESTUSER4'@'LOCALHOST' IDENTIFIED BY '1234';
    Query OK, 0 rows affected (0.02 sec)

    mysql> FLUSH PRIVILEGES;
    Query OK, 0 rows affected (0.01 sec)
    ```

+ 사용자 삭제
    ```mysql
    mysql> DROP USER 'TESTUSER4'@'LOCALHOST';
    Query OK, 0 rows affected (0.01 sec)

    mysql> FLUSH PRIVILEGES;
    Query OK, 0 rows affected (0.01 sec)
    ```

+ 사용자 모든 권한 주기 
    ```mysql
    mysql> GRANT ALL PRIVILEGES ON TESTDB.* TO 'TESTUSER1'@'LOCALHOST';
    Query OK, 0 rows affected (0.01 sec)

    mysql> GRANT ALL PRIVILEGES ON TESTDB.* TO 'TESTUSER2'@'LOCALHOST';
    Query OK, 0 rows affected (0.01 sec)

    mysql> GRANT ALL PRIVILEGES ON TESTDB.* TO 'TESTUSER3'@'LOCALHOST';
    Query OK, 0 rows affected (0.01 sec)

    mysql> FLUSH PRIVILEGES;
    Query OK, 0 rows affected (0.02 sec)
    ```

+ 테이블 생성 및 확인, 제거
    ```mysql
    mysql> 
        CREATE TABLE TESTTB(
            ID INT(11) NOT NULL AUTO_INCREMENT,
            NAME VARCHAR(20) NOT NULL,
            AGE VARCHAR(4) NULL,
            DATE DATETIME,
            CONSTRAINT TESTDB_PK PRIMARY KEY(ID)
        );
    Query OK, 0 rows affected, 1 warning (0.06 sec)

    mysql> DESC TESTTB;
    +-------+--------------+------+-----+---------+----------------+
    | Field | Type         | Null | Key | Default | Extra          |
    +-------+--------------+------+-----+---------+----------------+
    | ID    | int          | NO   | PRI | NULL    | auto_increment |
    | NAME  | varchar(20)  | NO   |     | NULL    |                |
    | AGE   | varchar(4)   | YES  |     | NULL    |                |
    | DATE  | datetime     | YES  |     | NULL    |                |
    +-------+--------------+------+-----+---------+----------------+

    mysql> SHOW TABLES;
    +------------------+
    | Tables_in_testdb |
    +------------------+
    | testtb           |
    +------------------+
    1 row in set (0.00 sec)

    mysql> DROP TABLE TESTTB;
    Query OK, 0 rows affected (0.04 sec)
    ```

+ 테이블 컬럼 추가, 변경, 삭제
    ```mysql
    mysql> ALTER TABLE TESTTB ADD ADDR VARCHAR(120) NULL AFTER AGE;
    Query OK, 0 rows affected (0.03 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    mysql> ALTER TABLE TESTTB MODIFY ADDR VARCHAR(220);
    Query OK, 0 rows affected (0.02 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    mysql> ALTER TABLE TESTTB DROP COLUMN ADDR;
    Query OK, 0 rows affected (0.03 sec)
    Records: 0  Duplicates: 0  Warnings: 0
    ```

+ 테이블 데이터 추가(INSERT)
    ```mysql
    mysql> INSERT INTO TESTTB (NAME, AGE, ADDR, DATE) VALUES ('PARK', 35, 'INCHEON', NOW());
    Query OK, 1 row affected (0.03 sec)

    mysql> INSERT INTO TESTTB (NAME, AGE, ADDR, DATE) VALUES ('LEE', 15, 'GUNSAN', NOW())
                , ('KIM', 32, 'YESAN', NOW())
                , ('CHOI', 33, 'JEJU', NOW());
    Query OK, 1 row affected (0.03 sec)
    ```

+ 테이블 데이터 수정(UPDATE)
    ```mysql
    mysql> UPDATE TESTTB SET NAME = 'HONG', AGE = 66 WHERE ID = 2;
    Query OK, 1 row affected (0.03 sec)
    Rows matched: 1  Changed: 1  Warnings: 0
    ```

+ 테이블 데이터 삭제(DELETE)
    ```mysql
    mysql> DELETE FROM TESTTB WHERE ID = 2;
    Query OK, 1 row affected (0.01 sec)
    ```

+ DATABASE EXPORT 내보내기
    ```cmd
    PS C:\dev\MySQL> mysqldump -u root -p TESTDB > testdb.sql 
    Enter password: ****
    ```

+ DATABASE IMPORT 가져오기
    ```cmd
    PS C:\dev\MySQL>mysql -u root -p testdb < testdb.sql
    Enter password: ****
    ```
    
    
