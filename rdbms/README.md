# Curso CEC Big Data TI 2020 - feb-mar-2020
## Por: Edwin Montoya, Universidad EAFIT, Medellín-Colombia
## emontoya@eafit.edu.co

# como poblar una base de datos mysql en AWS RDS desde estos scripts

1. crear una instancia EC2 - AMI 2 linux, para tener un cliente mysql. (name=clientmysql, keypair=bigdatati.pem)
2. crear una instancia AWS/RDS de Mysql - free tier (user: admin, password: bigdatati2020!)
3. entrar a la instancia 'clientmysql' y ejecutar:


        ACTUALIZAR EL hostname de la base de datos rds/mysql a la real:
        actualice: database-1.cj1yhistqein.us-east-1.rds.amazonaws.com

        $ sudo yum install mysql -y

        $ mysql -u admin –h database-1.cj1yhistqein.us-east-1.rds.amazonaws.com -p
        Enter password: bigdatati2020!
        mysql> create database cursodb;
        mysql> use cursodb;
        mysql> CREATE TABLE employee (  emp_id INT NOT NULL,  name VARCHAR(45),  salary INT,  PRIMARY KEY (emp_id));
        mysql> CREATE USER 'curso'@'%' IDENTIFIED BY 'curso';
        mysql> GRANT ALL PRIVILEGES ON cursodb.* TO 'curso'@'%';

        $ mysql –u curso –h database-1.cj1yhistqein.us-east-1.rds.amazonaws.com –p
        Enter password: curso
        mysql> use cursodb;
        mysql> insert into employee values (101, 'name1', 1800);
        mysql> insert into employee values (102, 'name2', 1500);
        mysql> insert into employee values (103, 'name3', 1000);
        mysql> insert into employee values (104, 'name4', 2000);
        mysql> insert into employee values (105, 'name5', 1600);
        Query OK, 1 row affected (0.00 sec)
        mysql> 

4. entrar a la instancia 'clientmysql', crear la bd 'retail_db' y cargar datos:

        descarga previamente el repo: https://github.com/ceceafit/bigdatati20201.git

        $ git clone https://github.com/ceceafit/bigdatati20201.git
        $ cd bigdatati20201/rdbms

        como administrador de la base de datos:

        $ mysql -u admin -h database-1.cj1yhistqein.us-east-1.rds.amazonaws.com -p < retail_db-ddl.sql

        como usuario: retail_dba:

        $ mysql -u retail_dba -h database-1.cj1yhistqein.us-east-1.rds.amazonaws.com -p retail_db < retail_db-data.sql
