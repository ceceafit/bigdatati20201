# Curso CEC Big Data TI 2020 - feb-mar-2020
## Por: Edwin Montoya, Universidad EAFIT, Medellín-Colombia
## emontoya@eafit.edu.co


# Amazon Glue + Athena

##  Amazon Glue

1. Crear un Glue - Crawler:

        crawler name: order data
        NEXT
        Data source: S3://orderlogs-ceceafit
        NEXT
        Create IAM Role: OrderData

        Frecuency: Run on command

        Add database: orderlogs

        corre manualmente el Crawler

        puede editar el esquema (scheme de la tabla creada asi)

        InvoiceNo
        StockCode
        Description
        Quantity
        InvoiceDate
        UnitPrice
        CustomerID
        Country
        year
        month
        day
        hour

        





