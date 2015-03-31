# mock-restful-express

A RESTful mock server powered by Express.js

## Table of Contents

1. [Purpouse](#Purpouse)
2. [Usage](#Usage)
3. [Project Routes](#Project Routes)
4. [Project Mocks](#Project Mocks)

## Purpouse

The purpose of this project is to provide a generic RESTful API server based on mocked responses, defined programatically and with support to many features like: 

- Basic Auth
- Cookies
- HTTP endpoints with support to GET, POST, PUT and DELETE actions

## Usage

### Project Routes

This project is based on the concepts of [Express.js routing](http://expressjs.com/guide/routing.html). Those features are provided by a library called [dynamic-routes](https://github.com/OneOfOne/dynamic-routes), and all routes can be defined programatically with support to all HTTP methods (GET, POST, PUT and DELETE) within the **routes** folder.

To know better these routes conventions, take a look on the project examples to understand the concepts. 

### Project Mocks

This project is also based on mocked responses, defined programatically in a convetional manner, within the **mocks** folder

#### Mocks path structure

The mocks path structure are the defined based on routes path. For example, suppose we have an /foo route defined on the project, with support to GET action. The respective mocked reponse path structure is defined as follows:

```
- mocks
|-- foo
|--- get
|---- all.json
|---- 1.json
|---- foo=bar.json
```

#### Mock response structure

All mock responses also are based on some conventions, defined in a structure as follows:

```json
{
	"code": 200,
	"content" : { "bar" }
}
```

This structure defines a response HTTP code (with support to all [HTTP codes](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes)) and payload, represented by **content** node.

#### Response for Path Param Request

A GET request on a route path with path param like **/foo/1** is conventionally mapped to *1.json* file, defined in a structure like shown below:

```
- mocks
|-- foo
|--- get
|---- 1.json
```

#### Response for Query Param Request

A GET request on a route path with query param like **/foo/?foo=bar&bar=foo**, its convetionally mapped to a *foo=bar&bar=foo.json* file, defined in a structure like shown below:

```
- mocks
|-- foo
|--- get
|---- foo=bar.json
```

#### Response for Subresource Request

A GET request on a route path defined for a subresource like **/foo/1/bar/2**, its convetionally mapped to a *1_2.json* file, defined in a structure like shown below:

```
- mocks
|-- foo
|--- bar
|---- get
|---- 1_2.json
```

#### Default responses

All requests are conventioned to have a defined mocked response
