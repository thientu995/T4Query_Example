# T4Query Example
Is project example of: https://www.nuget.org/packages/T4Query.SqlServer/

### Initialize the connection string
SqlData.ConnectionString = "data source=.\SqlExpress;initial catalog=TABLE_NAME;user id=USER_LOGIN;password=PASSWORD;MultipleActiveResultSets=True;App=EntityFramework";

### Initialize the SqlParameter (custom)
- SqlData.SetParameterTemplate(new System.Data.SqlClient.SqlParameter(...))

OR

- SqlData.SetParameterTemplate(

    new System.Data.SqlClient.SqlParameter(...)
    
    , new System.Data.SqlClient.SqlParameter(...)
    
    , new System.Data.SqlClient.SqlParameter(...)
    
    , ...
    
  )
  
OR

- SqlData.SetParameterTemplate(arrSqlParameter)

### Initialize SqlData
- new SqlData(STRING_QUERY)

OR

- new SqlData(STRING_QUERY, new System.Data.SqlClient.SqlParameter(...))

OR

- new SqlData(STRING_QUERY

    , new System.Data.SqlClient.SqlParameter(...)
    
    , new System.Data.SqlClient.SqlParameter(...)
    
    ,...
    
  )
  
- new SqlData(STRING_QUERY, arrSqlParameter)

### Initialize SqlData with System.Data.CommandType (Text, StoredProcedure or TableDirect)
Add parameter in position 2 with value: System.Data.CommandType.Text, System.Data.CommandType.StoredProcedure or System.Data.CommandType.TableDirect in SqlData.

EX: new SqlData(STRING_QUERY, System.Data.CommandType) or new SqlData(STRING_QUERY, System.Data.CommandType, new System.Data.SqlClient.SqlParameter(...)).

### Run Query
- ExecuteNonQuery: return the number of rows affected.

- ExecuteScalar<TSource>: return the first column of the first row in the result set, or a null if the result set is empty. Returns a maximum of 2033 characters.
  
- DataTable: return a DataTable that contains elements.

- DataSet: return a DataSet with select multiple table.

- IEnumerable<TSource>: return an enumerator that can be used to iterate through the collection.
  
- List<TSource>: A List that contains elements from the input sequence.
  
- FirstOrDefault<TSource>: return default(TSource) if source is empty; otherwise, the first element in source.
  
- Also, provide the SetDBNull (object) function: return DBNull.Value if object is null

EX: SqlData sql = new SqlData(STRING_QUERY).ExecuteDataTable()
