# How pyarrow writes 
## python
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

C++ _parquet is defined https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/_parquet.pyx#L2064 and it's write_table is 
here https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/_parquet.pyx#L2167

It essentially calls WriteTable on writer.https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/python/pyarrow/_parquet.pyx#L2181

writer is a FileWriter https://github.com/apache/arrow/blob/main/python/pyarrow/_parquet.pyx#L2066 

## cpp 
FileWriter is https://github.com/apache/arrow/blob/main/cpp/src/parquet/file_writer.cc

It's implementation is elsewhere in FileWriterImpl https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/cpp/src/parquet/arrow/writer.cc#L281

It implements WriteTable here https://github.com/apache/arrow/blob/ec41209ea02bdb410bc7e049cb3100afedf4ba2f/cpp/src/parquet/arrow/writer.cc#L367


# How pyarrow reads
