Install the mongdb package

Create a file to handle the database connection and return the database
```js
import { MongoClient } from 'mongodb';

const uri = process.env.MONGODB_URI;
const options = {
  useNewUrlParser: true,
  useUnifiedTopology: true,
};

let client;

// Connect to the MongoDB database
async function connectDatabase() {
  if (!client) {
    client = new MongoClient(uri, options);
    await client.connect();
  }
  return client.db();
}

export { connectDatabase };
```

Then import this connection to files where you intend to query the database.
```js
  const db = await connectDatabase();
  const collection = db.collection('movies');
  const movies = await collection.find().limit(10).toArray();
```