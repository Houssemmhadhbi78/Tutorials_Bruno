Links and notes about training on API Testing tutorials with Bruno

Lesson 1:
https://www.youtube.com/watch?v=_I4HhF-Fqsk
https://www.usebruno.com/downloads
========================================================================================================
Lesson 10 : https://www.youtube.com/watch?v=VBCHGsLbUKc&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=12

https://airportgap.com/tokens

Authentication Token created is: 
SEFUwhgiWvrJRKtJQGFfv6sY
Generate Token POST API: https://airportgap.com/api/tokens
{
	"email":"houssem.mhadhbi@etik.com",
	"password":"123Houssem&&"
}

Add Favorite API with POST request : https://airportgap.com/api/favorites
Use Body → Form URL Encoded and add these datas:
	airport_id=JFK
	note=My usual airport for New York trips
	
	airport_id=LHR
	note=My preferred airport for London travel
	
	airport_id=CDG
	note=Main airport I use when traveling to Paris
	
	airport_id=NRT
	note=Airport I use for Tokyo international flights

Get Favorite API with GET request : https://airportgap.com/api/favorites
========================================================================================================
Lesson 11 : https://www.youtube.com/watch?v=RMkycFlCv9E&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=11

API End point : https://postman-echo.com/digest-auth
Http methode:GET
Username:postman
Password:password
========================================================================================================
Lesson 12 : https://www.youtube.com/watch?v=a5tL0OfndQA&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=12

The query parameters are use to sort/filter resources.
LIST USERS:https://reqres.in/api/users?page=2
Http methode:GET
Reqres website: https://reqres.in/
========================================================================================================
Lesson 13 : https://www.youtube.com/watch?v=g8rSfyh64W4&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=13

Use of Vars(Variables) in Bruno
Vars allow you to set variables before request, and after you receive the response.
In the Pre Request Variables section, you can write any valid JavaScript expression.
The res object is variable, allowing you to declaratively parse the response and set variables , instead of writing scripts to do the same.
========================================================================================================
Lesson 14 : https://www.youtube.com/watch?v=WZO7LrT2vnI&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=14
Check Response Time of API 

Under Assert tab , add:

res.responseTime lte 1000

Under Tests tab , add:
test("response time test",function(){
  expect(res.getResponseTime()).to.lte(1000);
});
========================================================================================================
Lesson 15 : https://www.youtube.com/watch?v=DOtb89TK4Ds&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=15
How to use cURL command in Bruno?

What  is cURL?
cURL is a command line tool and library for transferring data with URLs.
Sample cURL command:

curl --location 'https://reqres.in/api/users'\
--header 'Content-Type:application/json'\
--data '{
	"name":"morpheus",
	"job":"learder"
	}'
========================================================================================================	
Lesson 16 : https://www.youtube.com/watch?v=Ge7VXEPRqzg&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=16
Use of Pre-Request & Post-Response Script in Bruno
These are added under Script tab .
Note:Pre-Request script will be executed before sending the request and Post-Response script will be executed after sending the request.

Pre-Request script eg:
To pass json payload as body:
req.setBody({
	"email":"houssem.mhadhbi@etik.com",
	"password":"123Houssem&&"
});
req.setBody({
	"email":"{{emailValue}}",
	"password":"{{passwordValue}}"
});
To pass Bearer token value as a header:
req.setHeader("Authorization","Bearer{{tokenValue}}");

Post-Response script eg:
bru.setVar("tokenValue",res.body.token);
========================================================================================================
Lesson 17 : https://www.youtube.com/watch?v=iYWNkM0u22U&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=20
Save API Response to a File in Bruno

We can save the reponse data for future reference, allowing you to store the results in various formats.
========================================================================================================
Lesson 18 : https://www.youtube.com/watch?v=nGCGeMCpyTQ&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=18
Use External NPM modules(Faker) in Bruno

How to use External librairies or any npm modules ( Faker) in Bruno.
Bruno supports loading any npm module to use in your scripting workflows.
1-You need to add a package.json file where your collection is stored.
package.json
{
  "name": "reqres-collection",
  "version": "1.0.0",
  "dependencies": {
    "@faker-js/faker": "8.3.1"
  }
}

2-You need to change in Bruno from Safe Mode to Developper Mode (Click the green shield).
( Developer Mode” would mean Bruno allows scripts to do advanced things like:
load local npm packages from node_modules
access filesystem if permitted
run non-default script behavior
So even if the label is not exactly “Developer Mode,” a trust/security/scripts permission switch may be the real equivalent.)

3-And then run npm install inside your collection folder:
npm install

4-Update bruno.json like this:
{
  "version": "1",
  "name": "Reqres",
  "type": "collection",
  "scripts": {
    "filesystemAccess": {
      "allow": true
    },
    "moduleWhitelist": [
      "@faker-js/faker",
      "path"
    ]
  },
  "ignore": [
    "node_modules",
    ".git"
  ]
}

5-And then you can require the node module in your script as usual. Example:

const { faker } = require('@faker-js/faker');
const randomName = faker.person.firstName();
const randomJob = faker.person.jobTitle();
req.setBody({
  name: randomName,
  job: randomJob
});
========================================================================================================
Lesson 19 : https://www.youtube.com/watch?v=oVxGA17xPW4&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=19
Generating code snippets from API requests

Bruno makes it easy to generate code snippets from your API requests, allowing you to quickly integrate and test your API in Various Programming languages.
This feature supports multiple languages (35+) and can help you save time when writing client code for your API.

========================================================================================================
Lesson 20 : https://www.youtube.com/watch?v=QVpYHS4Naro&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=20
Secret Management in Bruno

The video describes about different ways to manage secrets such as tokens, api keys and passwords in Bruno without exposing to outside world. In any collection, there are secrets that needs to be managed. These secrets can be anything such as API keys, passwords, or tokens. A common practice is to store these secrets in environment variables. There are two ways in which developers share bruno collections:

1. Check in the collection folder to source control (like git)
2. Export the collection to a file and share it

In both these cases we want to ensure that the secrets are 
stripped out of the collection before it is shared.

Bruno offers two approaches to manage secrets in collections.

1. DotEnv File
This approach is inspired by how usually developers manage secrets in their source code.
In this approach, you can store all your secrets in a .env file at the root of your
collection folder.Bruno will automatically load the secrets from this file and make them available
to your collection via process.env.secret-name
And now you can safely check in your collection to source control without worrying about 
exposing your secrets. Don't forget to add .env to your .gitignore file.

2. Secret Variables
In this approach, you can check the secret checkbox for any variable in your environment.
Bruno will manage your secrets internally and will not write them into the environment
file. And now you can safely check-in your collection to source control without worrying 
about exposing your secrets.When you export your collection as a file, Bruno will not 
export the secret variables.

========================================================================================================
Lesson 21 : https://www.youtube.com/watch?v=euZkdM9bcJ0&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=22
Passing Headers using Headers & Script tabs

What are headers?

HTTP headers contain metadata in key-value pairs that are sent along with 
HTTP requests and responses. They can be used to define caching behavior, facilitate authentication, 
and manage session state. HTTP headers help the API client and server communicate more effectively
and enable developers to optimize and customize the API’s behavior. 

1)Headers tab: 
Content-Type application/json 
Authorization Bearer {{replace here by actual token value}}

2)Script tab: 
// passing single header one by one 
req.setHeader( "content-type", "application/json"); 
req.setHeader( "Authorization", "Bearer {{replace here by actual token value}}"); 

// passing multiple headers 
req.setHeaders({ "content-type": "application/json", 
"Authorization": "Bearer {{replace here by actual token value}}" });

========================================================================================================
Lesson 22 : https://www.youtube.com/watch?v=RFWjFXigEXA&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=22
Filter with JSONPath Option in Bruno

To get complete airports details:
$.data

To get all airport names:
$.data[*].attributes.airport.name
$.data[*]..name

To get individual airport name:
$.data[0].attributes.airport.name
$.data[1].attributes.airport.name
$.data[0]..name
$.data[1]..name

To get all note values of airports:
$.[*].note
$.data..note

To get individual note values of airports:
$.data[0].attributes.note
$.data[1].attributes.note
$.data[0]..note
$.data[1]..note

To get first value:
$.links.first
$..first

========================================================================================================
Lesson 23 : https://www.youtube.com/watch?v=vJpcCWu4gjo&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=23
CRUD API | JSON Server | Localhost | in Bruno

Pre requisite: node.js and open CMD command
Installation:npm install -g json-server@0.17.4
db.json
{
  "posts": [
    {
      "id": 1,
      "title": "json-server",
      "author": "typicode"
    }
  ],
  "comments": [
    {
      "id": 1,
      "body": "some comment",
      "postId": 1
    }
  ],
  "profile": {
    "name": "typicode"
  }
}

Open CMD command from C:\Users\houss\JsonServer
Start server with:
json-server --watch db.json

========================================================================================================
Lesson 24 : https://www.youtube.com/watch?v=0etd1suxFds&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=24
Create Request Workflows bru.setNextRequest

By default, the collection runner (UI) and the CLI run requests in order. You can change the order by calling setNextRequest with the name of the next request to be run. This works
only in a post-request script or test-script.

Example:

bru.setNextRequest("RequestName");

You can also abort the run by explicitly setting the next request to null 

Example:

bru.setNextRequest(null); // aborts the run gracefully

bru.setNextRequest("Update Post");
bru.setNextRequest("Get Created Post");
bru.setNextRequest("Delete Created Post");
bru.setNextRequest(null);

========================================================================================================
Lesson 25 : https://www.youtube.com/watch?v=NwvU6HmDnG8&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=25
Use of getHeader & getHeaders methods

Added headers in headers tab in Bruno: 
headerKey1 headerValue1 
headerKey2 headerValue2 

Added javascript code in Script tab under pre request section: 

const headerValue1=req.getHeader("headerKey1"); 
console.log("headerValue1 is:",headerValue1); 
const headerValue2=req.getHeader("headerKey2"); 
console.log("headerValue2 is:",headerValue2); 
const headerValues=req.getHeaders(); 
console.log("headerValues are:",headerValues); 

Added javascript code in Script tab under post response section: 

const headerValue1=res.getHeader("connection");
console.log("headerValue1 is:",headerValue1); 
const headerValue2=res.getHeader("server"); 
console.log("headerValue2 is:",headerValue2); 
const headerValues=res.getHeaders(); 
console.log("headerValues are:",headerValues); 

Added test case to check header value under Tests tab: 
test("header value test", function() { expect(res.getHeader("connection")).to.equal("keep-alive"); });

========================================================================================================
Lesson 26 : https://www.youtube.com/watch?v=V3aXirUULOo&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=26
 how to use Auth, Headers, Scripts & Tests at collection level in Bruno and it's importance. 
 
========================================================================================================
Lesson 27 : https://www.youtube.com/watch?v=S-THB35FsPM&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=27
 Generate HTML Report using Bruno CLI . 
 
 Prerequisites:
Node.js
Check node version:node -v
Download:https://nodejs.org/en/download/current
Bruno CLI
installation command:npm install -g @usebruno/cli
To generate HTML report, open CMD inside the collection and run the command with environnement sitting:
bru run --env QA_Reqres --output results.html --format html

========================================================================================================
Lesson 29 : https://www.youtube.com/watch?v=BV2wkc3mOcI&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=28
How to use Path Parameter in Bruno. 

Path parameters are used to identify a specific resource or resources.

 Support added from version v1.19.0 in Bruno.

eg:https://reqres.in/api/users/2
http method:GET
Reqres website link: https://reqres.in/

========================================================================================================
Lesson 30 : https://www.youtube.com/watch?v=IzUqDY4i5c0&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=29
Migrating Postman collection to Bruno. 
To generate HTML report, open CMD inside the collection directory : "C:\Users\houss\Bruno_APis\MigratePostmanCollectionToBruno" and run the command with environnement sitting:
bru run --env Postman_Import_Env --output results.html --format html
========================================================================================================
Lesson 31 : https://www.youtube.com/watch?v=VzSVAnr2Uzc&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=30
Adding delay between API requests collection run. 

========================================================================================================
Lesson 32 : https://www.youtube.com/watch?v=VmSEaAKjQZw&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=31
The video describes about JavaScript Sandbox - Safe and Developer modes in Bruno.

Collections might include JavaScript code in Variables, Scripts, Tests, and Assertions.
Bruno take security seriously and want to ensure you can safely interact with collections, 
regardless of their source or original authors.

There are two modes you can choose from:

Safe Mode:
JavaScript code is executed in a secure sandbox and cannot access your filesystem or 
execute system commands. We recommend Safe Mode for most users.

Note: When in doubt, leave the Collection in Safe Mode. You can always switch to 
Developer Mode later.

Developer Mode:
JavaScript code has access to the filesystem, can execute system commands and access
sensitive information.

When to use Developer Mode?

You trust the collection source/authors (Ex: Collection maintained by you/your team) and Safe Mode
is not enough for your use case.
You need to use external npm packages in your scripts
Your collection needs access to filesystem / system commands

========================================================================================================
Lesson 33 : https://www.youtube.com/watch?v=UtF5P8uAL4c&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=32
 API Key Authentication | Direct Support| Auth Tab in Bruno.
 
========================================================================================================
Lesson 34 : https://www.youtube.com/watch?v=M8nV3cn6jxo&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=33
The video describes about adding Global environments and variables under the environment.

========================================================================================================
Lesson 35 : https://www.youtube.com/watch?v=-DoqBkVRmxI&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=35
Data Driven Testing using CSV file and Bruno CLI.

If you need to run a collection using data from a CSV file, specify the path to the file
 with the --csv-file-path option:
 
 bru run --csv-file-path data.csv
 bru run --csv-file-path data.csv --output result.html --format html
 The right CMD command on this directory: C:\Users\houss\Bruno_APis\DataDrivenTesting
 bru run --env baseUrlTDD --csv-file-path data.csv --output results.html --format html
 
Note: For open source users, this feature is only possible using Bruno CLI.
No option is available using the collection runner.

========================================================================================================
Lesson 36 : https://www.youtube.com/watch?v=CAowmD-sGTw&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=36
Data Driven Testing using JSON file and Bruno CLI .

If you need to run a collection using data from a CSV file, specify the path to the file
 with the --json-file-path option:
 
 bru run --json-file-path data1.json
 bru run --json-file-path data1.json --output result.html --format html
 
 The right CMD command on this directory: C:\Users\houss\Bruno_APis\DataDrivenTestingJSON
 bru run --env baseUrlTDD --json-file-path data1.json --output results.html --format html
 
Note: For open source users, this feature is only possible using Bruno CLI.
No option is available using the collection runner. 

========================================================================================================
Lesson 37 : https://www.youtube.com/watch?v=cH53C6rR6mg&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=37
Use of sleep() in Bruno.

sleep() pauses execution for the specified duration. This is useful for introducing delays or waiting for a specific amount of time before proceeding with the next operation.
await bru.sleep(3000);

========================================================================================================
Lesson 38 : https://www.youtube.com/watch?v=mrZyQ_NgsWs&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=38
Use of JSON Schema Validation with AJV npm package | Bruno API Client.

JSON Schema is a powerful tool used to describe and validate the structure of JSON data. It allows you to define what the data should look like,
specifying rules such as data types, required fields, and more. It is often used in API development to ensure that the data sent and received is valid according to the predefined rules.
Website to generate JSON Schema:https://www.liquid-technologies.com/online-json-to-schema-converter
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "name": {
      "type": "string"
    },
    "job": {
      "type": "string"
    },
    "id": {
      "type": "string"
    },
    "createdAt": {
      "type": "string"
    }
  },
  "required": [
    "name",
    "job",
    "id",
    "createdAt"
  ]
}

AJV:https://www.npmjs.com/package/ajv

Note: Replace draft-04 by draft-07, as ajv does not support draft-04 schema.

========================================================================================================
Lesson 39 : https://www.youtube.com/watch?v=Tw3sWirjlqE&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=39
GraphQL API Intro & Testing | Bruno API Client

The video describes  GraphQL API Introduction & Testing. GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables
powerful developer tools.
 
GraphQL Types:
 
Query - Retrieves data from the server. Queries specify the required data fields and can 
include arguments for more precise data retrieval.

Mutation - Manipulates data on the server, including creating, updating, or deleting records. 
Mutations specify the fields to be returned after the operation and use arguments to detail 
the manipulation.

Subscription - Gets real-time data updates from the server. Subscriptions enable clients to 
listen to specific data fields and receive updates automatically over a persistent connection.
 
When to use GraphQL vs. REST:
 
You can use GraphQL and REST APIs interchangeably. However, there are some use cases where 
one or the other is a better fit.

For example, GraphQL is likely a better choice if you have these considerations:

You have limited bandwidth, and you want to minimize the number of requests and responses
You have multiple data sources, and you want to combine them at one endpoint
You have client requests that vary significantly, and you expect very different responses

On the other hand, REST is is likely a better choice if you have these considerations:

You have smaller applications with less complex data
You have data and operations that all clients use similarly
You have no requirements for complex data querying

Eg: https://countries.trevorblades.com/

query GetCountry {
  country(code: "IN") {
    name
    native
    capital
    emoji
    currency
    languages {
      code
      name
    }
  }
}
or
query GetCountry {
  france: country(code: "FR") {
    name
    native
    capital
    emoji
    currency
    languages {
      code
      name
    }
  }
  india: country(code: "IN") {
    name
    native
    capital
    emoji
    currency
    languages {
      code
      name
    }
  }
}
========================================================================================================
Lesson 40 : https://www.youtube.com/watch?v=HuPnIKuA8RQ&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=40
Setting up of GraphQL Server for Testing. 

Install
npm install -g json-graphql-server
 
Create a db.js file.

module.exports = {
    posts: [
        { id: 1, title: "Lorem Ipsum", views: 254, user_id: 123 },
        { id: 2, title: "Sic Dolor amet", views: 65, user_id: 456 },
    ],
    users: [
        { id: 123, name: "John Doe" },
        { id: 456, name: "Jane Doe" }
    ],
    comments: [
        { id: 987, post_id: 1, body: "Consectetur adipiscing elit", date: new Date('2017-07-03') },
        { id: 995, post_id: 1, body: "Nam molestie pellentesque dui", date: new Date('2017-08-17') }
    ]
}

Start the GraphQL server on localhost, port 3000.
json-graphql-server db.js

To use a port other than 3000, you can run json-graphql-server db.js --p 4000

========================================================================================================
Lesson 41 : https://www.youtube.com/watch?v=fFz0lH-IA4Y&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=41
GraphQL Mutation Introduction & Testing. 

GraphQL mutations are operations that modify or change data on the server. While GraphQL queries
are used to retrieve data, mutations allow you to create, update, or delete data. 
They are defined in a schema just like queries, but they are typically used to 
perform write operations.

mutation CreatePost {
  createPost(title: "title1", user_id: "1", views: 10) {
    id
    title
    user_id
    views
  }
}

CreatePost-mutation name
createPost(title: "title1", user_id: "1", views: 10)-data passed along with mutation
id-expected json response from the server
title
user_id
views

========================================================================================================
Lesson 42 : https://www.youtube.com/watch?v=zzQ4uTzvbGY&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=42
Use of variables in GraphQL API. 

Variables in GraphQL allow for dynamic input to queries and mutations. They help make mutations reusable and prevent vulnerabilities like injection attacks. In GraphQL, variables are specified alongside the query or mutation itself. They allow for dynamic values to be passed into queries, instead of hardcoded into them.

mutation CreatePost($title: String!, $views: Int!, $user_id: ID!) {
  createPost(title: $title, views: $views, user_id: $user_id) {
    id
    title
    views
    user_id
  }
}

In this example:

CreatePost is the name of the mutation.
$title, $views and $user_id are variables specified with their required types (String!,Int! and ID! denote them as required arguments).
Inside the mutation, the variables are used as parameters (title: $title, views: $views, user_id: $user_id).
The $ symbol indicates that the field is specified by a variable.

{
  "title":"title1",
  "views":1,
  "user_id":"1"
}

========================================================================================================
Lesson 43 : https://www.youtube.com/watch?v=f58Wci3vU4Q&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=43
Reading Created data using query in GraphQL API.

query GetCreatedPost($id: ID!) {
  Post(id: $id) {
    id
    title
    views
    user_id
  }
}
Variables to add :
{
  "id": "4"
} 

========================================================================================================
Lesson 44 : https://www.youtube.com/watch?v=D5GsAfPoDwI&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=44
Updating data using mutation in GraphQL API.

mutation UpdatePost($id: ID!, $title: String, $views: Int, $user_id: ID!) {
  updatePost(id: $id, title: $title, views: $views, user_id: $user_id) {
    id
    title
    views
    user_id
  }
}

{
  "id":"5",
  "title":"title2",
  "views":1000,
  "user_id":101
}

========================================================================================================
Lesson 45 : https://www.youtube.com/watch?v=9f1M3V9agNk&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=45
Delete Created Data Mutation in GraphQL API.

mutation DeletePost($id: ID!){
  removePost(id: $id) {
    id
    title
    views
    user_id
  }
}

{
  "id":"5"
}

========================================================================================================
Lesson 46 : https://www.youtube.com/watch?v=-dwaqSxRTgw&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=46
Implementing request chaining in GraphQL API.

Request chaining refers to the practice of linking multiple API requests together, where the output
of one request is used as the input for subsequent requests. This is commonly done in situations
where the response of an earlier request provides data that is necessary for the next request in 
the sequence.

idValue - res.body.data.createPost.id

{
  "id": "{{idValue}}"
}

========================================================================================================
Lesson 47 : https://www.youtube.com/watch?v=UaFcre3Jv1U&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=47
What is GraphQL Subscription in GraphQL API.

In today’s digital landscape, where user expectations for real-time interactions continue to soar, GraphQL subscriptions provide a crucial link between conventional APIs and instantaneous data updates. GraphQL subscriptions are designed to facilitate real-time data exchange between clients and servers. They allow developers to create
applications that deliver live updates seamlessly, catering to the growing demand for dynamic content.

A GraphQL subscription typically resembles a regular query, but it is defined with the 
subscription keyword instead of the query or mutation keywords.
https://graphql.postman-echo.com/graphql

subscription Greetings{
  greetings
}

========================================================================================================
Lesson 48 : https://www.youtube.com/watch?v=y3PmbLAHnTo&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=48
Using custom JavaScript function directly in request body/payload with Bruno.

Under script tab on Pre-Request:

function getCurrentDate() {
  const currentDate = new Date();
  return currentDate.toLocaleDateString(); // 
}
bru.setVar("dateValue", getCurrentDate());

After that in body tab use as below:
{
    "name": "{{dateValue}}",
    "job": "leader"
}

========================================================================================================
Lesson 49 : https://www.youtube.com/watch?v=z3oTdZHO5j4&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=49
Send SOAP Webservices/requests in Bruno.

A SOAP (Simple Object Access Protocol) request is a way to send information from one application
to another using XML (eXtensible Markup Language). SOAP requests are often used to make remote calls over the internet. 
soap:https://www.w3schools.com/xml/tempconvert.asmx
http method: post
header:content-type text/xml

========================================================================================================
Lesson 50 : https://www.youtube.com/watch?v=rO-SGimSljE&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=50
Create API Documentation in Bruno.

Bruno allows you to create API documentation at three distinct levels: Request, Folder, and Collection.
With full Markdown support, you can write clear, concise, and well-structured documentation at each level supplemented with any relevant screenshots, gifs, or other elements to ensure 
your users have a seamless onboarding experience.

========================================================================================================
Lesson 51 : https://www.youtube.com/watch?v=23saWvzOoVg&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=51
Advanced Scripting get methods in Bruno.

bru.getCollectionVar("nameValue");
bru.getEnvName();
bru.getEnvVar("baseUrl");
bru.getFolderVar("foldervariable1");
bru.getGlobalEnvVar("baseUrl");
bru.getRequestVar("requesvar1");
bru.getProcessEnv("API_KEY");

========================================================================================================
Lesson 52 : https://www.youtube.com/watch?v=Iaf-FH_-OP0&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=52
Generate JSON Report in Bruno.

To generate a report in JSON format, use the --reporter-json option:
bru run --reporter-json results.json
If you need to use a specific environment, you can pass it with the --env option:
bru run --reporter-json results.json --env QA

========================================================================================================
Lesson 53 : https://www.youtube.com/watch?v=OmaX_v8kqxs&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=53
Generate JUnit Report in Bruno.

To generate a report in JUnit format, use the --reporter-junit option:
bru run --reporter-junit results.xml
If you need to use a specific environment, you can pass it with the --env option:
bru run --reporter-junit results.xml --env QA

The results.xml file will be in a format compatible with JUnit, making it ideal for
integration with CI/CD pipelines that rely on JUnit reporting.

========================================================================================================
Lesson 54 : https://www.youtube.com/watch?v=OgEypRV9HaY&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=54
Pass Environment Vars in Bruno.

Variables marked as secrets in Bruno app are not accessible via the CLI. Pass them directly as command-line arguments.
With this approach, collection can be run against different environments like QA, Dev, Stage etc.

bru run --env QA --env-var baseUrl=https://reqres.in/api

========================================================================================================
Lesson 55 : https://www.youtube.com/watch?v=nqnYzwyBEhI&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=56
Skipping Specific or All Headers in the HTML Report in Bruno.

Command to generate HTML Report : bru run --env QA --reporter-html  results.html

If you want to exclude certain headers(sensitive information) from the report, use
the --reporter-skip-headers option. You can list multiple headers to skip, separated by spaces.

bru run --env QA --reporter-html results.html --reporter-skip-headers "content-type" "connection" 

To exclude all headers from the report, use the --reporter-skip-all-headers option. This will remove all headers from the output report, ensuring a cleaner result.

bru run --env QA --reporter-html results.html --reporter-skip-all-headers

========================================================================================================
Lesson 56 : https://www.youtube.com/watch?v=l0MqHhZDKjo&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=57
Skipping Request during the Collection run in Bruno.

To skip the execution of the current request, use " bru.runner.skipRequest() " in the pre-request script section. This function is valid only within the context of a collection run.

========================================================================================================
Lesson 57 : https://www.youtube.com/watch?v=E9RPXbOW8Os&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=57
Create Env & Global variables using script in Bruno.

Use this code on Post Response in Script Tab to add a global variable:
bru.setGlobalEnvVar("globalToken", res.getBody().token); 

Or Use this code on Post Response in Script Tab to add a Environment variable:
bru.setGlobalEnvVar("globalToken", res.getBody().token); 

========================================================================================================
Lesson 58 : https://www.youtube.com/watch?v=sGkkqA4gwV4&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=58
File Upload - Multipart Form & Binary in Bruno.

https://www.postman.com/postman/published-postman-templates/documentation/ae2ja6x/postman-echo
https://www.postman-echo.com/post

========================================================================================================
Lesson 59 : https://www.youtube.com/watch?v=oSnAo2yyLgI&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=59
Sending URL Encoded Body Data in Bruno.

https://www.postman.com/postman/published-postman-templates/documentation/ae2ja6x/postman-echo
https://www.postman-echo.com/post
foo1 bar1
foo2 bar2

========================================================================================================
Lesson 60 :  https://www.youtube.com/watch?v=7PteqFkR4GA&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=60
Create collection from OpenAPI Specification in Bruno.

The OpenAPI Specification (OAS) provides a consistent means to carry information through each stage of the API lifecycle. 
It is a specification language for HTTP APIs that defines structure and syntax in a way that is not wedded to the programming language the API is created in. 
API specifications are typically written in YAML or JSON, allowing for easy sharing and consumption of the specification.
This can be done in 2 ways in Bruno
OpenAPI V3 URL
OpenAPI V3 File
https://api.apis.guru/v2/specs/adyen.com/CheckoutService/70/openapi.json

========================================================================================================
Lesson 61 :  https://www.youtube.com/watch?v=h-_EuJ5Fbpg&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=61
Bruno Continuous Integration with GitHub Actions.

Step 1: Configure Github Actions in the repo
a) Create bruno_test.yml file under .github/workflows in github. 
click on Actions tab and create a workflow
b) Add workflow to the file

Step 2: Setup Branch protection rules(Add classic branch)
a) Check Require a pull request before merging
b) Check Require approvals - 1
c) Check Require status checks to pass before merging - Execute Bruno CLI Tests
d) Check Do not allow bypassing the above settings

Step 3: Create new branch 'develop' and use HTMLReporter collection
git checkout -b develop
a) Make some changes in the collection and push the branch to repo.
b) Create a PR and add a reviewer(collaborator)
c) Reviewer should approve the PR
d) PR wil not be merged even after the apporoval since the workflow is failed
e) Correct the assertions and tests and raise PR again second commit with same branch 

Note: Report will be generated under the artifacts section.
This feature will allow developers to run the API tests ahead of deployment of application code, as 
bruno can store the collection in file system and it can be source controlled and kept in same
repo as that of application code.

========================================================================================================
Lesson 62 : https://www.youtube.com/watch?v=jUZ3aaJO6oM&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=62
GraphQL API Assertions & Tests | Bruno API Client 

Assertions

res.status 200
res.body.data.country.name India

Tests

test("status code test", function() {
expect(res.getStatus()).to.equal(200);
});
test("name data type test", function() {
expect(res.getBody().data.country.name).to.be.a('string');
});
test("name value test", function() {
expect(res.getBody().data.country.name).to.equal("India");
});
test("header value test", function() {
expect(res.getHeader("connection")).to.equal("keep-alive");
});

========================================================================================================
Lesson 63 : https://www.youtube.com/watch?v=OVXHNppyXT8&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=63
Dynamic Variables in Bruno.

Dynamic variables enable you to generate and use random data in your testing workflow. Bruno uses the faker.js library to generate random data. 
You can use these variables like any other variables in Bruno. The syntax to use dynamic variables is {{$randomData}}, and you can use
them in the request body, authentication, parameters, and other fields.

Note: Dynamic variables are case-sensitive and follow the camelCase convention.
Version:2.1.0
https://docs.usebruno.com/testing/script/dynamic-variables

{{$randomFullName}}
{{$randomJobTitle}}
{{$randomEmail}}

========================================================================================================
Lesson 64 : https://www.youtube.com/watch?v=OVXHNppyXT8&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=64
Timeline View in Bruno.

The Timeline tab provides detailed insights into the request’s response. It includes crucial information such as the body, authentication details, variables, parameters, headers, 
and other necessary data to inspect and validate the expected response. It also saves the request/response history and can view the detailed network logs.

========================================================================================================
Lesson 65 : https://www.youtube.com/watch?v=_GmD95Fr1P0&list=PL9ucy3ZNv-8A4evd-c8EaFt-F3nHd8xFR&index=65
Sharing Git synchronized collection via an embedded Fetch in Bruno button.

Bruno allows you to share your Git-synchronized collection via an embedded “Fetch in Bruno” (FiB) button turning the import/cloning process into a single click! This button can be placed in websites, articles, and documentation, with support for HTML and Markdown formats. This feature helps you to share your collections in an easy and flexible way - meeting the user wherever they are.
Once imported, the user now has a Git-synced collection and can seamlessly pull down new changes as updates are made.

Pre Requisites:
1.Bruno should be installed in your system.
2.A collection that has been initialized as a Git repository either through the UI or from the CLI.

Customizations
You can replace the Fetch in Bruno title and logo with your preferred logo and name. 
Simply follow the changes below in the markdown link:

Make sure to keep everything else as it is.