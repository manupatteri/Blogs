# Summary
Trying to document how Trino reads parquest
# Methods
## Method 1 ParquetReader
+ Code Reference - https://github.com/trinodb/trino/blob/master/lib/trino-parquet/src/main/java/io/trino/parquet/reader/ParquetReader.java
+ ParquetReader constructor without parquetPredicate, columnIndexStore and writeValidation is used by IcebergPageSourceProvider.
+ ParquetReader constructor with parquetPredicate, columnIndexStore and writeValidation is used by HudiPageSourceProvider, ParquetPageSourceFactory(in trino-hive), ParquetWriter(for validation) .and ParquetTestUtils.
+ 
