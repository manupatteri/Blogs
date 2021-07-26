# Introduction
Iceberg is a newer table format which should help avoid non-standard hive format. For years all other SQL projects have been trying to follow hive format without hive format being standardized and documented. 
Iceberg seems to be adding some more capabilities which I am yet to explore. 

# Setup
For setup I used test setup mentioned in https://trino.io/episodes/14.html under section 'Demo: Creating tables with Iceberg and reading the data in Trino
'. 

Setup and running is also explained here https://www.youtube.com/watch?v=CEKz8JvfxuE&t=4333s 

Basic steps like below didn't work for me. Solution described below.

    git clone git@github.com:bitsondatadev/trino-getting-started.git
    cd iceberg/trino-iceberg-minio


## Issues
### Docker not exposing Minio port

# Run tests
