## PyODBC
* odbc_python_config.py
```
odbc_connection = 'DRIVE={Oracle in OraClient12Home1}; DBQ = xxxx.ttt.com:1234/serverName; Uid=userid; Pwd=password'
```
* pyodbc usage
```
sys.path.append('path that include file odbc_python_config.py')
import odbc_python_config
ODBC_Oracle = odbc_python_config.odbc_connection

connection = pyodbc.connect(ODBC_Oracle)
dataset = pd.DataFrame()
parameters = [a,b,c,d,e,f]
placeholders = ", ".join(["?"] * len(parameters)) 
sql_query = (
  """
  select aaa
  from bbb
  where ccc in (""" + placeholders + """)
  """
  )
dataset = pd.read_sql(sql_query, connection, params = parameters)
connection.close()
```

