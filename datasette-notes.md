# Host Data in Datasette

## Start database

```console
New-Item test.db
```

## Create the db and load a CSV

```console
sqlite-utils insert test.db varieties "Z:\crop-varieties\data\Dummy_dataset\Final_Dummy_data_set\merged_long_final.csv" --csv
```

## Inspect upload

```console
sqlite-utils tables test.db --schema --table
```

## Run datasette

```console
datasette test.db -p 8002
```
_Note: Default port is 8001_

## Open locally

```console
http://localhost:8002
```
