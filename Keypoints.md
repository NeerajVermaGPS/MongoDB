<img src="https://webimages.mongodb.com/_com_assets/cms/kuyjf3vea2hg34taa-horizontal_default_slate_blue.svg" height="70">

## MongoDB: Open source, document based and NoSQL database management system.

Here is a guide I have prepared for MongoDB Basics. Feel free to provide your valuable additions:


### Connect to MongoDB:

1. **Install** MongoDB Compass, CLI, Database Tools
2. **Add PATH** for Database tools similar to this: `"C:\Program Files\MongoDB\Tools\100\bin"`
3. **Start the MongoDB Database server** in Task Manager Services
4. **Run ```mongosh```** in your command prompt


### Database Operations:

1. **show dbs or show databases:** Show all databases
2. **use db_name:** Creates or selects db_name
3. **db.dropDatabase():** Deletes current database and 


### Collection Operations:

1. **show collections:** Show all collections
2. **db.createCollection('cl_name'):** Creates new collection cl_name
3. **db.cl_name.drop():** Deletes cl_name
4. **db.cl_name.insertOne({data}):** Inserts one data in cl_name if the collection exists or first creates cl_name if doesn't exists
5. **db.cl_name.insertMany([{data1}, {data2},...]):** Similar to insertOne but inserts multiple data
6. **db.cl_name.find():** Prints complete data of a collection
6. **db.cl_name.find({'key':'value'}):** Prints complete data that matches the given condition from a collection
6. **db.cl_name.findOne({'key':'value'}):** Prints first document that matches the given condition from a collection
7. **db.cl_name.insertMany([{data1}, {data2},...], {ordered:false}):** Ordered false will throw an error if any document of the insertion is not correct and will insert other documents, by default it is set to true.
8. Everything in MongoDB is **case-sensitive**.


### MongoDB Imports/Exports:

**Note:** This import and export will be out of the mongo shell. And the *maximum JSON document size being imported should be 16 megabytes*.

1. **mongoimport "absolute_path\file_name.json" -d db_name -c cl_name:**
Imports the complete json document if it is in following format:

    ```json
    {"name":"Ms. Autumn Skiles","email":"katherine60@madam.com","address":"81323 Simone Flats Apt. 695\nSouth Lucileville, CO 24991","phone":"+1 (648) 391-8320","website":"https://madam.com"}
    {"name":"Mrs. Reba Heathcote","email":"kboyer@madam.info","address":"13859 Pasquale Mountain Suite 734\nSouth Dayneview, WA 27288","phone":"619.230.2594","website":"https://madam.com"}
    {"name":"Prof. Dale Schiller IV","email":"dbrown@madam.com","address":"461 Hand Rapid\nLake Angeloville, KS 45943","phone":"(830) 797-0870 x597","website":"https://madam.com"}
    ```
    Sample Reference: [View](https://github.com/NeerajVermaGPS/MongoDB/blob/master/Resources/1mb.json)


2. **mongoimport "absolute_path\file_name.json" -d db_name -c cl_name --jsonArray:**
Imports the complete json document if it is in following format:

    ```json
    [
        {"name":"Ms. Autumn Skiles","email":"katherine60@madam.com","address":"81323 Simone Flats Apt. 695\nSouth Lucileville, CO 24991","phone":"+1 (648) 391-8320","website":"https://madam.com"},
        {"name":"Mrs. Reba Heathcote","email":"kboyer@madam.info","address":"13859 Pasquale Mountain Suite 734\nSouth Dayneview, WA 27288","phone":"619.230.2594","website":"https://madam.com"},
        {"name":"Prof. Dale Schiller IV","email":"dbrown@madam.com","address":"461 Hand Rapid\nLake Angeloville, KS 45943","phone":"(830) 797-0870 x597","website":"https://madam.com"}
    ]
    ```
    Sample Reference: [View](https://github.com/NeerajVermaGPS/MongoDB/blob/master/Resources/4mb.json)


3. **mongoexport -d db_name -c cl_name -o "absolute_path\file_name.json"**:
Exports the data from cl_name collection of db_name to file_name.json in following format:

    ```json
    {"_id": { "$oid": "66d2e3e4400a7ea85d228fb6" },"name": "Madam","phone": "5823542342","grades": "A++"}
    {"_id": { "$oid": "66d2e3e4400a7ea85d228fb7" },"name": "Madam2","phone": "3894232301","grades": "A+"}
    ```
    Sample Output: [View](https://github.com/NeerajVermaGPS/MongoDB/blob/master/Resources/export_simple.json)


4. **mongoexport -d db_name -c cl_name -o "absolute_path\file_name.json" --jsonArray**
Exports the data from cl_name collection of db_name to file_name.json in following format:

    ```json
    [
        {"_id": { "$oid": "66d2e3e4400a7ea85d228fb6" },"name": "Madam","phone": "5823542342","grades": "A++"},
        {"_id": { "$oid": "66d2e3e4400a7ea85d228fb7" },"name": "Madam2","phone": "3894232301","grades": "A+"}
    ]
    ```
    Sample Output: [View](https://github.com/NeerajVermaGPS/MongoDB/blob/master/Resources/export_array.json)


---
### Some Additional Points:

1. MongoDB uses Storage Engine, which works as a layer between MongoDB database and persistent storage. Example of storage engines: MMAPv1, Wired Tiger.
1. Storage engine stores document in BSON(Binary JSON) format, which looks like this:

    **JSON:**
    ```json
    [
        {"_id": { "$oid": "66d2e3e4400a7ea85d228fb6" },"name": "Madam","phone": "5823542342","grades": "A++"},
        {"_id": { "$oid": "66d2e3e4400a7ea85d228fb7" },"name": "Madam2","phone": "3894232301","grades": "A+"}
    ]
    ```

    **BSON:**
    ```bson
    0xdb 0x00 0x00 0x00 0x03 0x30 0x00 0x68 0x00 0x00 0x00 0x03 0x5f 0x69 0x64 0x00 0x28 0x00 0x00 0x00 0x02 0x24 0x6f 0x69 0x64 0x00 0x19 0x00 0x00 0x00 0x36 0x36 0x64 0x32 0x65 0x33 0x65 0x34 0x34 0x30 0x30 0x61 0x37 0x65 0x61 0x38 0x35 0x64 0x32 0x32 0x38 0x66 0x62 0x36 0x00 0x00 0x02 0x6e 0x61 0x6d 0x65 0x00 0x06 0x00 0x00 0x00 0x4d 0x61 0x64 0x61 0x6d 0x00 0x02 0x70 0x68 0x6f 0x6e 0x65 0x00 0x0b 0x00 0x00 0x00 0x35 0x38 0x32 0x33 0x35 0x34 0x32 0x33 0x34 0x32 0x00 0x02 0x67 0x72 0x61 0x64 0x65 0x73 0x00 0x04 0x00 0x00 0x00 0x41 0x2b 0x2b 0x00 0x00 0x03 0x31 0x00 0x68 0x00 0x00 0x00 0x03 0x5f 0x69 0x64 0x00 0x28 0x00 0x00 0x00 0x02 0x24 0x6f 0x69 0x64 0x00 0x19 0x00 0x00 0x00 0x36 0x36 0x64 0x32 0x65 0x33 0x65 0x34 0x34 0x30 0x30 0x61 0x37 0x65 0x61 0x38 0x35 0x64 0x32 0x32 0x38 0x66 0x62 0x37 0x00 0x00 0x02 0x6e 0x61 0x6d 0x65 0x00 0x07 0x00 0x00 0x00 0x4d 0x61 0x64 0x61 0x6d 0x32 0x00 0x02 0x70 0x68 0x6f 0x6e 0x65 0x00 0x0b 0x00 0x00 0x00 0x33 0x38 0x39 0x34 0x32 0x33 0x32 0x33 0x30 0x31 0x00 0x02 0x67 0x72 0x61 0x64 0x65 0x73 0x00 0x03 0x00 0x00 0x00 0x41 0x2b 0x00 0x00 0x00
    ```
---

### Important Resources:

1. [MongoDB official documentation](https://www.mongodb.com/docs/manual/)
2. [Read about MongoDB Architecture](https://www.mongodb.com/lp/resources/products/fundamentals/mongodb-architecture-guide)

### Happy Coding!
**Visit my portfolio: [https://neerajvermagps.infinityfreeapp.com/](https://neerajvermagps.infinityfreeapp.com/)**