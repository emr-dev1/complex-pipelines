# Complex Pipelines

This was created to gain a better understanding for processing large sets of data using Go.

- The three processes:
    - Data Producer Process
        - reads input data and sends that to a destination for further processing
    - Data Consumer Process
        - receives raw data, parses those values using the expected format and sends them to a different process
    - Persistent Storage Process
        - receives parsed data and stores that in batches

## Running the Program

Ensure you have a database running locally:

```
docker run -d --rm \
  -e POSTGRES_HOST_AUTH_METHOD=trust -e POSTGRES_DB=complex_pipeline \
  -p 5432:5432 --name complex_pipeline postgres:alpine
```

Create table by connecting to the container

```
docker exec -it complex_pipeline psql -U postgres -d complex_pipeline
```

Execute the SQL statement:

```sql
CREATE TABLE "public"."names" (
	"nconst"              varchar(255),
	"primary_name"        varchar(255),
	"birth_year"          varchar(4),
	"death_year"          varchar(4) DEFAULT '',
	"primary_professions" varchar[],
	"known_for_titles"    varchar[]
);
```

Run the program:

```
DATABASE_URL="postgres://postgres:@127.0.0.1:5432/complex_pipeline" go run main.go
```