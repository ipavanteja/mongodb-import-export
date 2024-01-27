# MongoDB-Import-Export

To import a database from MongoDB Atlas to your local MongoDB instance, you can use the `mongodump` and `mongorestore` tools. Here are the general steps:

### 1\. Export Data from MongoDB Atlas:

Run the following command to export the data from MongoDB Atlas. Replace `<ATLAS_CONNECTION_STRING>` with your MongoDB Atlas connection string:

```nginx
mongodump --uri "<ATLAS_CONNECTION_STRING>" --gzip --archive=dump.gz
```

This command creates a compressed archive file (`dump.gz`) containing the exported data.

### 2\. Copy Data to Your Local Machine:

Copy the exported data to your local machine. You can use tools like `scp` (Secure Copy Protocol) or any other preferred method:

```nginx
scp user@your_remote_server_ip:/path/to/dump.gz /path/on/your/local/machine/
```

Replace `user` with your remote server's username, `your_remote_server_ip` with your remote server's IP address, `/path/to/dump.gz` with the path to the dump file on your remote server, and `/path/on/your/local/machine/` with the destination path on your local machine.

### 3\. Import Data to Your Local MongoDB:

Run the following command to import the data to your local MongoDB instance:

```nginx
mongorestore --gzip --archive=/path/on/your/local/machine/dump.gz
```

Replace `/path/on/your/local/machine/dump.gz` with the actual path to the dump file on your local machine.

### Want to use just `mongodump` to download data in WSL ? Try this

#### Install MongoDB Tools in WSL:
- Open your WSL terminal.
- Run the following commands to install the MongoDB tools:

```nginx
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 656408E390CFB1F5
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
sudo apt-get update
sudo apt-get install -y mongodb-org-tools
```

This will install the MongoDB tools package, which includes mongodump.

#### Verify Installation:

After the installation is complete, verify that mongodump is now available by running:

```nginx
mongodump --version
```

You should see the version information for mongodump, indicating that the command is now recognized.
Now you should be able to run your [export-data-from-mongodb-atlas:](https://github.com/ipavanteja/mongodb-import-export/blob/main/README.md#1-export-data-from-mongodb-atlas) command:

## MongoDB shell commands

Below are some common MongoDB shell commands with clear examples. Please note that these examples assume a basic understanding of MongoDB concepts like databases, collections, documents, etc.

### 1\. Connect to MongoDB:

```nginx
mongosh
```

### 2\. Show Databases:

```nginx
show dbs
```

### 3\. Switch to a Database:

```nginx
use your_database_name
```

### 4\. Show Collections in the Current Database:

```nginx
show collections
```

### 5\. Insert a Document:

```javascript
db.your_collection_name.insertOne({ key: 'value' })
```

### 6\. Query Documents:

```javascript
db.your_collection_name.find()
```

### 7\. Update a Document:

```javascript
db.your_collection_name.updateOne({ key: 'value' }, { $set: { new_key: 'new_value' } })
```

### 8\. Delete a Document:

```javascript
db.your_collection_name.deleteOne({ key: 'value' })
```

### 9\. Create an Index:

```javascript
db.your_collection_name.createIndex({ field_name: 1 })
```

### 10\. Show Query Execution Plan:

```javascript
db.your_collection_name.find({ key: 'value' }).explain('executionStats')
```

### 11\. Aggregate Data:

```javascript
db.your_collection_name.aggregate([

  { $group: { _id: '$field_name', total: { $sum: 1 } } },

  { $sort: { total: -1 } }

])
```

### 12\. Drop a Database:

```nginx
use your_database_name

db.dropDatabase()
```

### 13\. Drop a Collection:

```javascript
db.your_collection_name.drop()
```

### 14\. Backup and Restore (mongodump/mongorestore):

- Dump a database:

```nginx
mongodump --uri "your_mongodb_uri" --gzip --archive=dump.gz
```

- Restore a database:

```nginx
mongorestore --gzip --archive=dump.gz
```

### 15\. Exit MongoDB Shell:

```nginx
exit
```
These commands cover various MongoDB operations. Adjust the collection names, database names, and field names based on your specific MongoDB setup. For more detailed information and advanced features, you can refer to the [MongoDB documentation](https://www.mongodb.com/docs/).
