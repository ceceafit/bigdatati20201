# Curso CEC Big Data TI 2020 - feb-mar-2020
## Por: Edwin Montoya, Universidad EAFIT, Medellín-Colombia
## emontoya@eafit.edu.co


# Amazon Kinesis labs

1. crear un servicio kinesis firehose por la consola web:

        Create: Delivery streaming data with Kinesis Firehose
        Name: purchaseLogs
        Source: Direct PUT or other sources
        Use: Kinesis Agent
        Destination:
        Amazon S3 – select or create a bucket (orderlogs-ceceafit)
        S3 buffer conditions: 
        Buffer interval: 60 segs
        IAM role:
        Create new: ‘firehose_delivery_role’ with defaults

2. crear una instancia EC2 AMI2 linux

3. instalar el agente kinesis

        $ sudo yum install –y https://s3.amazonaws.com/streaming-data-agent/aws-kinesis-agent-latest.amzn1.noarch.rpm

4. descargar los logs ejemplo y LogsGenerator.py (ya estan en el github)

5. cambiar permisos, crear directorios, etc:

        $ chmod a+x LogGenerator.py
        $ sudo mkdir /var/log/acmeco
        $ sudo nano /etc/aws-kinesis/agent.json

6. iniciar el agente:

        $ sudo systemctl start aws-kinesis-agent

7. ejecutar un envio de logs:

        $ sudo ./LogGenerator.py 500000

8. chequee en unos minutos el 'bucket' orderlogs-ceceafit
