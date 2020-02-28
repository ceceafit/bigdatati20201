# Curso CEC Big Data TI 2020 - feb-mar-2020
## Por: Edwin Montoya, Universidad EAFIT, Medellín-Colombia
## emontoya@eafit.edu.co

# como poblar una base de datos mysql en AWS RDS desde estos scripts

1. crear una instancia EC2 - AMI 2 linux, para tener un cliente mysql. (name=clientmysql, keypair=bigdatati.pem)
2. crear una instancia AWS/RDS de Mysql - free tier (user: root, password: bigdatati2020!)
3. entrar a la instancia 'clientmysql' y ejecutar:


        $ mysql -u root –h database-1.cj1yhistqein.us-east-1.rds.amazonaws.com -p
        Enter password: bigdatati2020!
        mysql> create database cursodb;
        mysql> use cursodb;
        mysql> CREATE TABLE employee (  emp_id INT NOT NULL,  name VARCHAR(45),  salary INT,  PRIMARY KEY (emp_id));
        mysql> CREATE USER 'curso'@'%' IDENTIFIED BY 'curso';
        mysql> GRANT ALL PRIVILEGES ON cursodb.* TO 'curso'@'%';

        $ mysql –u curso –h database-1.cj1yhistqein.us-east-1.rds.amazonaws.com –p
        Enter password: curso
        mysql> use cursodb;
