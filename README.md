# SleekDB
Brief presentation about SleekDB and also a quick tutorial on how to install, run and use it.

## Table of contents:
1. [What is SleekDB?](#what-is-sleekdb)
   1. [Features and Advantages](#features-and-advantages)
   2. [Query Life Cycle in SleekDB](#query-life-cycle-in-sleekdb)
2. [Installation](#installation)
   1. [Requirements](#requirements)
   2. [Composer Installation](#composer-installation)
   3. [Getting Started in 4 steps](#getting-started-in-4-steps)
3. [Understanding the SleekDB basics](#understanding-the-sleekdb-basics)
   1. [Managing Store](#managing-store)
   2. [Insert Data](#insert-data)
   3. [Fetch Data](#fetch-data)
   4. [Edit Data](#edit-data)
   5. [Delete Data](#delete-data)
4. [THX 4 ATTENTION](#thx-4-attention)

## What is SleekDB?
__SleekDB - A NoSQL Database made using PHP.__ SleekDB is a simple flat file NoSQL like database implemented in PHP without any third-party dependencies that store data in plain JSON files.

It is not comparable with databases like Sqlite, MySQL, PostgreSQL and MariaDB because they are relational databases! SleekDB is a NoSQL database and therefore more comparable with for example MongoDB.

It is not designed to handle heavy-load IO operations, it is designed to have a simple solution where all we need a database for is managing a few gigabytes of data. You can think of it as a database for low to medium operation loads.

### Features and Advantages
- __⚡ Lightweight & Fast.__ <br>
Stores data in plain-text utilizing JSON format, no binary conversion needed to store or fetch the data. Default query cache layer.
- __🔆 Schema free data storage.__ <br>
SleekDB does not require any schema, so you can insert any types of data you want.
- __🔍 Query on nested properties.__ <br>
As it supports schema free data, so you can filter and use conditions on nested properties of the JSON documents!
- __✨ Dependency free, only needs PHP to run.__ <br>
Supports PHP 7+. Requires no third-party plugins or software.
- __🚀 Default caching layer.__ <br>
SleekDB will serve data from cache by default and regenerate cache automatically! Query results will be cached and later reused from a single file instead of traversing all the available files.
- __🌈 Rich Conditions and Filters.__ <br>
Use multiple conditional comparisons, text search, sorting on multiple properties and nested properties.
- __👍 Process data on demand.__ <br>
SleekDB does not require any background process or network protocol in order to process data when you use it in a PHP project. All data for a query will be fetched at runtime within the same PHP process.
- __💩 Runs everywhere.__ <br>
Runs perfectly on shared-servers or VPS too.
- __🍰 Easy to learn and implement.__ <br>
SleekDB provides a very simple elegant API to handle all of your data.
- __💌 Actively maintained.__ <br>

 
### Query Life Cycle in SleekDB
Term | Query Life Cycle
--- | ---
`1. Store` | The Store class is the first, and in most cases also the only part you need to come in contact with.
`2. QueryBuilder` | The QueryBuilder class is used to prepare a query. To execute it getQuery method can be used.
`3. Query` | At this step the Query class contains all information needed to execute the query.
`4. Cache` | The Cache class handles everything regarding caching. It will decide when to cache or not to cache.

## Installation

### Requirements
Extension | Insctruction
--- | ---
`PHP >= 7.0` | installed on pc
`Composer` | installed on pc
`ext-json` | unable in php.ini
`ext-mbstring` | unable in php.ini

### Composer Installation
 To install SleekDB using composer, open a terminal, cd into your project root directory and run this
 <pre> composer require rakibtg/sleekdb</pre>

### Getting Started in 4 steps
- 1. To start, create in your root directory `index.php` file
- 2. Write a ✨Magic code✨ in `index.php` file.
- 3. Run a Server, enter in terminal <pre> php -S localhost:8000 </pre>
- 4. Follow the link to see a results [`localhost:8000`](http://localhost:8000/)

## Understanding the SleekDB basics

### Managing Store

- __Setting the store configuration__
<pre>$storeConfiguration = [
  "auto_cache" => true,
  "cache_lifetime" => null,
  "primary_key" => "_id",
  "search" => [
    "min_length" => 2,
    "mode" => "or",
    "score_key" => "scoreKey",
    "algorithm" => Query::SEARCH_ALGORITHM["hits"]
  ]
];</pre>

- __Creating a store__

<pre>use SleekDB\Store;
use SleekDB\Query;
$databaseDirectory = __DIR__."/database";

$todoStore = new Store('todos', $databaseDirectory,$storeConfiguration);</pre>

- __Insert a new todo in store__
<pre>$todoStore->insert([
  'description' => 'todo example',
  'status' => 'active'
]);</pre>

- __Show the content of $todoStore__
<pre>$allTodos = $todoStore->findAll();
//let see all todos we have
echo json_encode($allTodos);</pre>

- __Delete a store__
<pre>$todoStore->deleteStore();</pre>

### Insert Data

- __insert__
<pre>// Prepare a PHP array to insert.
$todo = [
    'description' => 'show how insert query works',
    'status' => 'done'
];
// Insert the data.
$todo = $todoStore->insert($todo);</pre>

- __insertMany__
<pre>// Prepare a PHP array to insert.
$todo = [ 
         [
           'description' => 'show how insertMany query works (part1)',
           'status' => 'active'
         ],
         [
           'description' => 'show how insertMany query works (part2)',
           'status' => 'done'
         ]  
        ];
// Insert the data.
$todo = $todoStore->insertMany($todo);</pre>

### Fetch Data

- __findAll__
<pre>
$allTodos = $todoStore->findAll();
echo json_encode($allTodos);
</pre>

- __findBy__
<pre>
$todosBy = $todoStore->findBy(["description", "=", "active"]);
echo json_encode($todosBy);
</pre>

- __findById__
<pre>
$todosById = $todoStore->findById(1);
echo json_encode($todosById);
</pre>

### Edit Data

- __update__
<pre>$todoUpdate = [
    'description' => 'Read this sentence to the end',
    'status' => 'active'
];
//store the todo
$todoStore->insert($todoUpdate);
// retrieve a todo
$todoUpdate = $userStore->findBy(['description', '=', 'show how insertMany query works (part1)']);
// update todo
$todoUpdate["status"] = "done";
// updates the todo by using his _id
$todoStore->update( $todoUpdate ); </pre>

- __updateById__
<pre>$todoStore->updateById(1, [ 'description' => 'finish the presentation', 'status' => 'active']);
// lets take a look on a result
$todosById = $todoStore->findById(1);
echo json_encode($todosById);
</pre>

### Delete Data

- __deleteBy__
<pre>$userStore->deleteBy(["status", "=", "done"]);
// lets see that all todos with done status was removed
$allTodos = $todoStore->findAll();
echo json_encode($allTodos);
</pre>

- __deleteById__
// now lets finish the presentation 
<pre>$userStore->deleteById(1);

$allTodos = $todoStore->findAll();
echo json_encode($allTodos);
</pre>

# THX 4 ATTENTION
<img src="https://media0.giphy.com/media/3o7TKC2GLMWQC7PqiA/giphy.gif?cid=ecf05e47aajji9v4u7x63vlwhxj96t2wn6bnloce90hvuarm&rid=giphy.gif&ct=g" width="1000" height="500"></img>
