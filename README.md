Base JAX-RS Api [![Build Status](https://travis-ci.org/dancastellani/jax-rs-base-api.png?branch=master)](https://travis-ci.org/dancastellani/jax-rs-base-api)
=============== 
This is a base code to improve implementation velocity to implement Jax-RS APIs. 
With tt you get all default REST routes for your API just extending the `BaseApi` class and implementing some methods.


Why?
---
JAX-RS is very verbose to define the routes and this is repeated to each API you want to provide. 
All REST resources have the same interface:

__REST routes to resource__

| HTTP Verb | Path           | Action       | Used for                             | API Method | 
| :---------|:-------------- |:-------------| :------------------------------------| :----------|
| GET       | /resources     | index (list) | display a list of all resource items | list       |
| POST      | /resources     | create       | create a new resource item           | create     |
| GET       | /resources/:id | show         | display a specific resource item     | show       |
| PUT       | /resources/:id | update       | update a specific resource item      | update     |
| DELETE    | /resources/:id | destroy      | delete a specific resource item      | delete     |

Thus, with this project you dont need to re-write the routes definition to each resource API, just implement what they do.

Ruby on Rails is a very good example of the easyness to implement a API's controller when using conventions.


How to use it?
---
Yout API must extend the abastract class [`BaseApi`](https://github.com/dancastellani/jax-rs-base-api/blob/master/src/main/java/br/danielcastellani/jaxrsbase/api/BaseApi.java), implementing its abstract methods. 
Also, the exceptions you want to throw in API must extend `ApiException`.

__Maven Dependency__
Add to your pom.xml:
<pre>
  &lt;dependency>
    &lt;groupId>br.danielcastellani&lt;/groupId>
    &lt;artifactId>base-jax-rs-api&lt;/artifactId>
    &lt;version>1.0-SNAPSHOT&lt;/version>
  &lt;/dependency>
</pre>

__Get Dependency__
Since it is not on Maven Central, yet, you must run in your machine:
<pre>
git clone https://github.com/dancastellani/jax-rs-base-api.git
cd jax-rs-base-api
mvn install
</pre>

How it works?
---
JAX-RS-Base-Api has a abastract class [`BaseApi`](https://github.com/dancastellani/jax-rs-base-api/blob/master/src/main/java/br/danielcastellani/jaxrsbase/api/BaseApi.java) and a exception `ApiException`. 
The [`BaseApi`](https://github.com/dancastellani/jax-rs-base-api/blob/master/src/main/java/br/danielcastellani/jaxrsbase/api/BaseApi.java) defines the routes above for each API that extends it. 
Each route calls a abstract method that must be implemented. These methods are:


* __list__()
* __show__(int i)
* __create__(T t)
* __delete__(int i)
* __update__(Integer intgr, T t) 

