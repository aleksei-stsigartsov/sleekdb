# SleekDB
Brief presentation about SleekDB and also a quick tutorial on how to install, run and use it.

## Table of contents:
1. [What is SleekDB?](#what-is-sleekdb)
   1. [Features and Advantages](#features-and-advantages)
   2. [Key terms](#key-terms-used-in-sleekdb)
2. [Installation](#installation)
   1. [Requirements](#requirements)
   2. [Composer Installation](#composer-installation)
   3. [Getting Started in 4 steps](#getting-started-in-4-steps)
3. [Understanding the SleekDB basics](#understanding-the-sleekdb-basics)
   1. [Managing Store](#managing-store)

## What is SleekDB?
__SleekDB - A NoSQL Database made using PHP.__ SleekDB is a simple flat file NoSQL like database implemented in PHP without any third-party dependencies that store data in plain JSON files.

It is not comparable with databases like Sqlite, MySQL, PostgreSQL and MariaDB because they are relational databases! SleekDB is a NoSQL database and therefore more comparable with for example MongoDB.

It is not designed to handle heavy-load IO operations, it is designed to have a simple solution where all we need a database for is managing a few gigabytes of data. You can think of it as a database for low to medium operation loads.

### Features and Advantages
- __⚡ Lightweight & Fast.__ Stores data in plain-text utilizing JSON format, no binary conversion needed to store or fetch the data. Default query cache layer.
- __🔆 Schema free data storage.__ SleekDB does not require any schema, so you can insert any types of data you want.
- __🔍 Query on nested properties.__ As it supports schema free data, so you can filter and use conditions on nested properties of the JSON documents!
- __✨ Dependency free, only needs PHP to run.__ Supports PHP 7+. Requires no third-party plugins or software.
- __🚀 Default caching layer.__ SleekDB will serve data from cache by default and regenerate cache automatically! Query results will be cached and later reused from a single file instead of traversing all the available files.
- __🌈 Rich Conditions and Filters.__ Use multiple conditional comparisons, text search, sorting on multiple properties and nested properties.
- __👍 Process data on demand.__ SleekDB does not require any background process or network protocol in order to process data when you use it in a PHP project. All data for a query will be fetched at runtime within the same PHP process.
- __💩 Runs everywhere.__ Runs perfectly on shared-servers or VPS too.
- __🍰 Easy to learn and implement.__ SleekDB provides a very simple elegant API to handle all of your data.
- __💌 Actively maintained.__

 
### Key terms used in SleekDB
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
 <pre> composer require rakibtg/sleekdb`</pre>

### Getting Started in 4 steps
- 1. To start see a results, create in your root directory `index.php` file
- 2. Do a ✨Magic code✨ in `index.php` file.
- 3. Run a Server, enter in terminal `php -S localhost:8000`
- 4. Follow the link [`localhost:8000`](http://localhost:8000/)

## Understanding the SleekDB basics

### Managing Store

- __Creating a store__
<pre>use SleekDB\Store;
$todoStore = new Store('todos', $dataDir);</pre>

- __Insert a new todo in store__
<pre>$todoStore->insert([
  'description' => 'todo example',
  'status' => 'active'
]);</pre>

- __Delete a store__
<pre>$todoStore->deleteStore();</pre>


