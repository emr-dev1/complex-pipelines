# Complex Pipelines

This was created to gain a better understanding for processing large sets of data using Go.

- The three processes:
    - Data Producer Process
        - reads input data and sends that to a destination for further processing
    - Data Consumer Process
        - receives raw data, parses those values using the expected format and sends them to a different process
    - Persistent Storage Process
        - receives parsed data and stores that in batches
