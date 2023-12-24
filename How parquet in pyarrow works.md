# How pyarrow writes 
We use pyarrow.parquet. 
Then we use write_table.
write_table code is at https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/parquet/core.py#L1857.
Python code itself depends on ParquetWriter. (That doesn't look like a Python class)
# How pyarrow reads
