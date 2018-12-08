# An example

```
public static void example()
{
    SqlLiteDatabase db = new SqlLiteDatabase("connectionString_to_yourdb");
    db.Process((connection, transaction) =>
    {
        SqlLiteDatabase.Query(
            "select TEST_VAL1,TEST_VAL2 from TEST_TABLE where TEST_VAL1 = @val1",
            new (String, object)[]{("@val1","abcdef")},
            connection,
            transaction,
            (result) => {
                while (result.Next())
                {
                    var resultValues = result.ResultValues;
                    Console.Out.WriteLine("TEST_VAL1:" + resultValues.TEST_VAL1);
                    Console.Out.WriteLine("TEST_VAL2:" + resultValues.TEST_VAL2);
                }
            }
        );
    });
}
```

