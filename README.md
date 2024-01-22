# mongodb-import-export

To import a database from MongoDB Atlas to your local MongoDB instance, you can use the `mongodump` and `mongorestore` tools. Here are the general steps:

### 1\. Export Data from MongoDB Atlas:

Run the following command to export the data from MongoDB Atlas. Replace `<ATLAS_CONNECTION_STRING>` with your MongoDB Atlas connection string:

```bash
mongodump --uri "<ATLAS_CONNECTION_STRING>" --gzip --archive=dump.gz
```

This command creates a compressed archive file (`dump.gz`) containing the exported data.

### 2\. Copy Data to Your Local Machine:

Copy the exported data to your local machine. You can use tools like `scp` (Secure Copy Protocol) or any other preferred method:

```bash
scp user@your_remote_server_ip:/path/to/dump.gz /path/on/your/local/machine/
```

Replace `user` with your remote server's username, `your_remote_server_ip` with your remote server's IP address, `/path/to/dump.gz` with the path to the dump file on your remote server, and `/path/on/your/local/machine/` with the destination path on your local machine.

### 3\. Import Data to Your Local MongoDB:

Run the following command to import the data to your local MongoDB instance:

```bash
mongorestore --gzip --archive=/path/on/your/local/machine/dump.gz
```

Replace `/path/on/your/local/machine/dump.gz` with the actual path to the dump file on your local machine.
