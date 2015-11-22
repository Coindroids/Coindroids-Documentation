---
title: API Introduction
tags: [API, Introduction, Conventions]
keywords: json, droid, object, patch, get, post, api, rest, events 
last_updated: November 21, 2015
summary: "An introduction to the Coindroids REST API"

---


### HTTP Methods
|Name|Description|
|---|---|
|GET | Retrieve objects |
|POST| Create new objects |
|PATCH| Update existing object(s) |
|DELETE| Deletes one or more objects |
|OPTIONS| Describe the object and receive a programmatic version of this document | 


### Filtering Rows

Any column in a table can be filtered or ordered through URL query parameters. For instance, to return all droids under the Heavy class:

```HTTP
GET /droid?droid_class=eq.Heavy
```

Adding multiple parameters conjoins the conditions, here we include the initial class requirement along with a level less than 10:

```HTTP
GET /droid?droid_class=eq.Heavy&level=lt.10
```

These operators are available:

<table>
<thead>
<tr><th>abbreviation</th><th>meaning</th></tr>
</thead>
<tbody>
<tr><td><code>eq</code></td><td>equals</td></tr>
<tr><td><code>gt</code></td><td>greater than</td></tr>
<tr><td><code>lt</code></td><td>less than</td></tr>
<tr><td><code>gte</code></td><td>greater than or equal</td></tr>
<tr><td><code>lte</code></td><td>less than or equal</td></tr>
<tr><td><code>neq</code></td><td>not equal</td></tr>
<tr><td><code>like</code></td><td>LIKE operator (use * in place of %)</td></tr>
<tr><td><code>ilike</code></td><td>ILIKE operator (use * in place of %)</td></tr>
<tr><td><code>@@</code></td><td>full-text search using <code>to_tsquery</code></td></tr>
<tr><td><code>is</code></td><td>checking for exact equality (null,true,false)</td></tr>
<tr><td><code>isnot</code></td><td>checking for exact inequality</td></tr>
<tr><td><code>in</code></td><td>one of a list of values e.g. `?a=in.1,2,3`</td></tr>
<tr><td><code>notin</code></td><td>none of a list of values e.g. `?a=notin.1,2,3`</td></tr>
</tbody>
</table>

To negate any operator prefix it with `not` like `?a=not.eq=2`. The custom negative operators like `neq` are deprecated and will be removed in version three.

For more complicated conditions, joins, or statistical functions you will have to create a new view in the database.

_[Original Source](https://github.com/begriffs/postgrest/wiki/Routing)_


