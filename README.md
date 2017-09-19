# FME® MongoDBObjectIDGenerator
## About
Generates new MongoDB Document ID's (also known as BSON ObjectID's) or validates existing ones.  
A BSON ObjectID is a 12 byte binary string that is built up as follows:

- a 4-byte value representing the seconds since the Unix epoch,  
- a 3-byte machine identifier,  
- a 2-byte process id, and  
- a 3-byte counter, starting with a random value.

However, this transformer will validate/generate its 24 character hexadecimal string equivalent.

**Why use this transformer?**  
Although FME's MongoDB writer will generate MongoDB ID's automatically, there might be a case where you want to create documents that reference other documents by ObjectID. Therefore, you would need to generate an ID in advance, that will be written to the _mongodb_id_ attribute. Note that you should rename this attribute (to anything you like) on the document feature if it uses this ObjectID _as a foreign key_ (i.e. the "child"). Otherwise, the writer uses the ObjectID on both the "parent" and the "child" document as a _primary key_, which will fail.

### Notes
- Also available on [FME Hub](https://hub.safe.com/transformers/mongodbobjectidgenerator) for convenient installation.  
- This transformer uses the Node.js abilities of the [JavaScriptCaller](https://www.safe.com/transformers/java-script-caller/), which currently is a beta feature of FME.  
- There are no dependencies, because the code to generate the ObjectID's has been embedded. The original code can be found [here](https://github.com/mongodb/js-bson/blob/1.0-branch/lib/bson/objectid.js).  
- Released under [GNU General Public License v3.0](https://github.com/SanderSchaminee/fme-mongodbobjectidgenerator/blob/master/LICENSE).  
- If you notice a bug or desire a new feature, please contact me. Or make a pull request!  
- [This FME workspace](https://github.com/SanderSchaminee/fme-mongodbobjectidgenerator/blob/master/MongoDBObjectIDGeneratorTest.fmw) is used for testing and provides some examples.
