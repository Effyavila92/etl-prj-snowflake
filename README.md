# `Building an ETL with Apache Airflow and Snowflake with Python, PostgreSQL and data visualization using Microsoft Power BI`

This project aims to take the information of a dataset from the government's open data page to create an ETL process from Jupyter with Python, using airflow to orchestrate the process to the data warehouse that will be Snowflake, where it will then be stored in a DB using PostgreSQL and finally visualized in Power BI, all through a simple architecture, as shown below.

## Project architecture:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d7600817-85c4-44a6-a327-03f8160dd106/Untitled.png)

# 1. Main tools

- Get the dataset from an official government page: [https://www.datos.gov.co/Educaci-n/MEN_ESTADISTICAS_EN_EDUCACION_EN_PREESCOLAR-B-SICA/ji8i-4anb/data](https://www.datos.gov.co/Educaci-n/MEN_ESTADISTICAS_EN_EDUCACION_EN_PREESCOLAR-B-SICA/ji8i-4anb/data)

Get the information from the page, through ***SODA API:*** Provides the standardization for Data / Storage Management APIs. · This is the key external interface to platforms:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6106d462-3efe-4cde-aea8-3c11276eae56/Untitled.png)

- Get an IDE to manage data, Ej: JetBrains - DataGrip ([https://www.jetbrains.com/es-es/datagrip/](https://www.jetbrains.com/es-es/datagrip/))
- Get GitBash.

## STEP BY STEP

1. Create a folder to store the project from the console

*NOTE: Use snake_case : use _ instead of space and all in minus.*

```bash
mkdir etl-prj-snowflake
```

1. Create a virtual environment.

NOTE: Virtual environments or **venv** allow Python installations or tweaks to run only on that specific project and not on Windows in general.

1. From the console create the venv (it is the second venv shown, the first one is the command), it is recommended to keep the same name.

```sql
python -m venv venv
```

1. Proceed to activate it so that it is shown in the upper part of the console path, to do so run:

```sql
source venv/Scripts/activate
```

It may looks like this:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7e63632-1265-497f-895e-d4cfc115008c/Untitled.png)

1. Once the venv is created, the repository must be created.

### Creating the repository:

Primero se debe crear el repo desde el disco local del pc, para luego, hacer un git push de manera remota a GitHub.

Desde la consola, ubicarse en la ruta del venv creado y luego ejecutar:

```sql
git init
```

now appears in the path of the console, the word (main) that indicates that this branch has been created locally where the project will be stored.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0db09a1f-93ef-4a1c-bd10-8e4ff8c79f72/Untitled.png)

From the local creation of the repository, some folders are created with it by default in the project folder, among them the .gitignore file, this allows to enter everything that should not be accessed from the remote repo in GitHub, it is there where the venv must be put, for it:

1. Abrir el archivo .gitignore desde la consola:

```bash
vim .gitignore
```

It appears like this:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/08962e60-e1b9-406e-88ac-3671bd9a194a/Untitled.png)

1. Press the I = INSERT key and type the word venv/ to enter it and prevent the virtual environment from being visible from the remote repo.
2. Press esc to stop editing and then :wq, (save and close).

NOTE: To see what we have installed in Python in the project run:

```python
pip freeze
```

## Installing Jupyter in our venv

Link to Jupyter:

[http://localhost:8888/notebooks/etl-snowflake.ipynb](http://localhost:8888/notebooks/etl-snowflake.ipynb)

1. This intermediate step requires the use of the Jupyter tool, which must be installed from the console to use it.

```sql
pip install jupyter
```

*NOTE: It will take about 5 minutes to complete the whole process.*

1. After installing, open a new tab in the console, since the current one will be running Jupyter and will not allow you to do anything different from it.
2. From the console type the word **Jupyter notebook** to open the program from Google Chrome.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0ed61ec3-bfe8-418a-a42e-033a789a0ef1/Untitled.png)

*NOTE: From the browser URL you can identify that you are working from the local disk.*

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43cff453-7b40-4ba1-a88c-218472223ce5/Untitled.png)

1. From Jupyter, create a Python work window from the New button:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/049fa1b1-ab8e-4f33-98cf-8dc3f8abbe9e/Untitled.png)

## Jupyter

Now we will import the information from the web page to Jupyter, to do so:

1. Import the libraries needed for the project:

```python
import pandas as pd
```

Relevance of the libraries in the project:

- Pandas: Essential for working with data in Python

*NOTE: As these libraries did not exist in venv, they must also be installed from the local console:*

```python
pip install pandas
```

1. Once the library has been imported, the URL variable containing the path to the data on the web page must be declared:

```bash
url = "https://www.datos.gov.co/resource/ji8i-4anb.json"
```

1. Now the following line of code must be used to read the resource using pandas as pd.

```bash
df = pd.read_json(url)
```

1. Visualize information:

```bash
df.head()
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d9f98c2-9149-4ef5-bcee-1f771905b2ee/Untitled.png)

Enviar los datos de Jupyter a Snowflake