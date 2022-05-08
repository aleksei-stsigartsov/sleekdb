# SleekDB
Brief presentation about SleekDB and also a quick tutorial on how to install, run and use it.

## Table of contents:
1. [What is SleekDB?](#what-is-sleekdb)
   1. [Features and Advantages of SleekDB](#features-and-andvantages-of-sleekdb)
   2. [Key terms](#key-terms-used-in-sleekdb)
2. [Installation](#installation)
   1. [Getting Started](#getting-started)
3. [Understanding the SleekDB basics](#understanding-the-sleekdb-basics)
   1. [Managing Store](#managing store)

## What is SleekDB?
__SleekDB - A NoSQL Database made using PHP.__ SleekDB is a simple flat file NoSQL like database implemented in PHP without any third-party dependencies that store data in plain JSON files.

It is not comparable with databases like Sqlite, MySQL, PostgreSQL and MariaDB because they are relational databases! SleekDB is a NoSQL database and therefore more comparable with for example MongoDB.

It is not designed to handle heavy-load IO operations, it is designed to have a simple solution where all we need a database for is managing a few gigabytes of data. You can think of it as a database for low to medium operation loads.

### Features and Advantages of SleekDB
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
Term | Usage
--- | ---
`Title` | Text.




