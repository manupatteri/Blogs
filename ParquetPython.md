# Introduction
Two options I could find was using either pyarrow or fastparquet. Ultimately my intention is to create a parquet where one or more columns have byte_stream_split encoding.  
# Data preparation
In all options, data can be  prepared using well known python libraries such as numpy, pandas etc. Here is some sample code. 
    import pyarrow.parquet as pq
    import pyarrow as pa
    import pandas as pd
    import numpy as np

    df = pd.DataFrame({'one': [-1, 3.14, 2.5], 'two': ['foo', 'bar', 'baz'], 'three': [True, False, True]}, index=list('abc'))
    table = pa.Table.from_pandas(df)

pyarrow table can be easily written to file which we will see below. 

# Writing parquet files
## pyarrow
As name suggests, pyarrow is a python library which supports managing Arrow memory format. Since both Arrow and Parquet came from same authors probably even parquet 
management can be done via pyarrow. 

### Write as table
Earlier I thought that this is a higher level API  and it doesn't have all options when compared to directly using ParquetWriter. As I was reading documentation again for preparing this note, I noticed that write_table also can accept arguments which can help create column with byte_stream_split. 
    
    #Simple file write
    pq.write_table(table, 'example.parquet')
    
### Write using ParquetWriter

    writer = pq.ParquetWriter('writer.parquet', schema=table.schema, use_dictionary=False,compression="gzip", use_byte_stream_split=True)
    writer.write_table(table)
    #Since we are dealing with raw APIs, things like closing file object is left upon us. 
    writer.close()

## fastparquet
This is a Parquest specific library. TODO

# Reading parquet files
```
import pyarrow.parquet as pq

parquet_table = pq.read_table('example.parquet')

print(parquet_table.to_pandas())

```


