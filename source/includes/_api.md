

# API Conventions

What do droids love almost as much as a good ol' fashioned money fight? A full-featured API of course!

<aside class='success'>
Anything that can be accomplished through our site can be done through the API. Our site is actually powered by the same API. 
</aside>

## HTTP Methods
|Name|Description|
|---|---|
|GET | Retrieve objects |
|POST| Create new objects |
|PATCH| Update existing object(s) |
|DELETE| Deletes one or more objects |
|OPTIONS| Describe the object and receive a programmatic version of this document | 

<aside class="warning">
<b>Connection problems?</b>
<br>If you have issues validating our certificate, you may need to install the <a href='https://www.alphassl.com/support/install-root-certificate.html'>AlphaSSL Intermediate CA</a>.
</aside>


## Filtering Rows

> Filtering Rows

```shell
curl -X "GET" "http://api.coindroids.com/droid?name=eq.Trunk"
```

> Filtering with multiple conditions 

```shell
curl -X "GET" "http://api.coindroids.com/droid?purse_current=gt.1000&level=lt.10"
```


Any column in a table can be filtered or ordered through URL query parameters.

These conditions can also be changed with an &amp;. 


### Available operators

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

## Filtering Columns

```shell
curl -X "GET" "http://api.coindroids.com/droid?select=name,id,attack_address"
```

> To cast the column types, add a double colon

```shell
curl -X "GET" "http://api.coindroids.com/droid?select=level::text,name,id"
```

You can customize which columns are returned using the `select` parameter:

<aside class='warning'>
Not all type coercions are possible, and you will get an error describing any problems from selection or type casting.
</aside>

## Ordering



The reserved word `order` applies an `ORDER BY` clause.  It uses a comma-separated list of columns and directions:

```shell
curl -X "GET" "http://api.coindroids.com/droid?order=level.asc,purse_current.desc"
```

If no direction is specified it defaults to descending order:

```shell
curl -X "GET" "http://api.coindroids.com/droid?order=level"
```




