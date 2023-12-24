# How pyarrow writes 
We use pyarrow.parquet. 

We use write_table in pyarrow.parquet.

write_table code is at https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/parquet/core.py#L1857.

Python code itself depends on ParquetWriter. (That doesn't look like a Python class)

Turns out it is a python class https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/parquet/core.py#L929

ParquetWrite.write_table is here https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/parquet/core.py#L1080

It hands it off to write_table from writer. https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/parquet/core.py#L1104

self.writer is an object created here https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/parquet/core.py#L1010C36-L1010C36. 

It uses a ParquetWriter from _parquet.

_parquet is pyarrow._parquet. Ref: https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/parquet/core.py#L33

That seems to be coming from cpython code. https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/_parquet.pyx

Which means its in C++ code. 

# How pyarrow reads
