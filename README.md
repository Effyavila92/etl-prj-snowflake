# `Building an ETL with Apache Airflow and Snowflake with Python, PostgreSQL and data visualization using Microsoft Power BI`

This project aims to take the information of a dataset from the government's open data page to create an ETL process from Jupyter with Python, using airflow to orchestrate the process to the data warehouse that will be Snowflake, where it will then be stored in a DB using PostgreSQL and finally visualized in Power BI, all through a simple architecture, as shown below.

## Project architecture:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d7600817-85c4-44a6-a327-03f8160dd106/Untitled.png)

Pasos 1 al 14 son iguales que en el pry anterior, excepto que en este por el momento solo se instala pandas

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d9f98c2-9149-4ef5-bcee-1f771905b2ee/Untitled.png)

[https://www.datos.gov.co/Educaci-n/MEN_ESTADISTICAS_EN_EDUCACION_EN_PREESCOLAR-B-SICA/ji8i-4anb/data](https://www.datos.gov.co/Educaci-n/MEN_ESTADISTICAS_EN_EDUCACION_EN_PREESCOLAR-B-SICA/ji8i-4anb/data)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6106d462-3efe-4cde-aea8-3c11276eae56/Untitled.png)

Enviar los datos de Jupyter a Snowflake

SODA API, punto de acceso a través de la URL