# REST Cheatsheet

**[TL;DR — Show me the routes!](#routes-for-resources-that-are-collections-and-members)**

### 1. A definition of REST

In short, here is our working definition of REST:

> REST is **a series of best practices for how one should write interfaces   
> on the web**. It enforces a specific format for using HTTP verbs and URI  
> paths to interact with that data.

Here is the vocabulary that we use when discussing RESTful interaction:

| Term                    | Definition 
|:-------------------:    |:-----------
| **interface**           | The list of input/output options, or **routes**, made available by our server. 
| **path**                | A path refers to the portion of a URL that follows the domain name, i.e. `/movies/5` in the URL `http://cinemaniacs.com/movies/5`
| **route**               | A route is a combination of an HTTP **verb** (GET, POST, PUT, or DELETE) and a **path**. 
| **HTTP verb**           | Also known as a method, a description of what to do with a resource. 
| **resource**            | The **intended conceptual target of a request**; either a **single** piece of data, a **collection** of data, or any **member** of a collection of data. 
| **single resource**     | A singular resource that is not a member of a collection (eg, a title of something). 
| **collection resource** | A resource with many instances (eg, a library). 
| **member resource**     | A singular resource that is part of a collection (eg, a book). 
| **unique ID**           | Every resource must have some way to refer to it, either by name, number, or some combination of both, that is unique! 


### 2. Implementing RESTful interfaces <div name="rest-as-interface"></div>

As a client, **we can only do one of four things with a server**, known by the unfortunate mnemonic **CRUD**. We can:

- request that it store some resource, ie **Create** data (`POST`),
- request that it retrieve a resource it's storing, ie **Read** data (`GET`),
- request that it change a resource it's storing, ie **Update** data (`PUT`/`PATCH`), or
- request that it remove a resource it's storing, ie **Delete** data (`DELETE`).

Our most common request is to read, or `GET`, resources that the server stores! Links are all `GET` requests, for example.

The other requests are performed mostly by forms. While the HTML specification (*HTML, not HTTP!*) has yet to fully include support for `PUT`, `PATCH` and `DELETE`, we can use *method overriding* in our applications to use these forms with an HTTP `POST` and still direct the request to the correct route within our server.

---

#### Routes for resources that are collections and members

The most common case is that there are **multiple instances of the resource**.

In this case, the resource is accessed as a ***collection*** and its ***members***, with these seven routes:

| Purpose                                                          | HTTP Verb | Simple URI Path*          | Action   | Template Name
|:--------                                                         |:----------|:----------------          |:--:      | :------------
| Display all instances of a resource (collection).                | `GET`     | `resources`               | render   | resources/index
| Ask for a form to create a new resource instance (member).       | `GET`     | `resources/new`           | render   | resources/new
| Tell the server to create a new resource instance (member).      | `POST`    | `resources`               | redirect | 
| Display a specific resource instance (member).                   | `GET`     | `resources/member_id`     | render   | resources/show
| Ask for a form to update or delete a resource instance (member). | `GET`     | `resources/member_id/edit`| render   | resources/edit
| Tell the server to make changes to a resource instance (member). | `PUT`**   | `resources/member_id`     | redirect | 
| Tell the server to delete a resource instance (member).          | `DELETE`  | `resources/member-id`     | redirect | 

<sub>&ast; – NOTE THAT THE RESOURCE NAME ABOVE IS **ALWAYS PLURAL!**</sub>   
<sub>&ast;&ast; – CAN ALSO BE USED WITH `PATCH`, BUT THE DISTINCTION IS NOT IMPORTANT TO THIS DISCUSSION</sub>   

---

#### Routes for single resources










If there is only **one instance of our resource**, it is accessed as a single resource with these six routes:

| Purpose                                                            | HTTP Verb  | Simple URI Path* | Action   | Template Name
|:--------:                                                          |:---------- |:---------------- |:--:      | :------------
| Display the resource.                                              | `GET`      | `resource`       | render   | resource/show
| Ask for a form to update or delete the resource.                   | `GET`      | `resource/edit`  | render   | resource/edit
| Tell the server to make changes to the resource.                   | `PUT`      | `resource`       | redirect | 
| Ask for a form to create the resource. Rarely used in this way.**  | `GET`      | `resource/new`   | render   | resource/new
| Create the resource. Rarely used in this way.**                    | `POST`     | `resource`       | redirect | 
| Tell the server to delete the resource.**                          | `DELETE`   | `resource`       | redirect |  

<sub>&ast; – NOTE THAT THE RESOURCE NAME ABOVE IS **ALWAYS SINGULAR!**</sub>   
<sub>&ast;&ast; – WHILE WE SOMETIMES CREATE OR DESTROY SINGULAR RESOURCES, IT'S RARE. WE ALMOST NEVER HAVE A *NEW* FORM.</sub>   

---

#### Examples

<!-- Assume that our host is accessed either as:

- `http://www.hostname.tld`, or
- `http://localhost`,

... and that all the below paths are referenced from the root of our domain. -->

**If our application has a single profile that stores the user's preferences...**

When we want to look at the profile, we will link to (SHOW):

```
GET /profile
```

When we want to update the profile to include a new preference, we will navigate to (EDIT):

```
GET /profile/edit
```

... which should have a form that will send a request to (UPDATE):

```
PUT /profile
```

**If our application allows users to upload fanfiction stories...**

When we want to create a new *fanfic*, we will navigate to (NEW):

```
GET /fanfics/new
```

... which should have a form that will send a (CREATE) request to:

```
POST /fanfics
```

... and can redirect us to display to the (SHOW) page at:

```
GET /fanfics/45
```

... where '45' is the new unique ID for the fanfic story.

If we saw that we misspelled Jean-Luc Picard's name in our fanfic, then we can fix it by navigating to (EDIT):

```
GET /fanfics/45/edit
```

... where our form will submit our changes to (UPDATE):

```
PUT /fanfics/45
```

We can then get embarrassed about our fanfic story and remove it, by sending a (DELETE) request to:

```
DELETE /fanfics/45
```

Finally, we can browse the list of every fanfic to make sure our story is no longer there:

```
GET /fanfics
```

---

### 4. REST as an idea <div name="rest-as-idea"></div>

REST is a big idea, and means a lot of things to a lot of people. Finding good, clear, information for those learning web development is very difficult. Much of what REST is about concerns the basic structure of the web and therefore is beyond the scope of this class. To read more about that, you can always visit the three major "resources" :) we point you to in class:

1. [REST on Wikipedia][wikipedia-definition]. A very good summary, actually.
2. [Ryan Tomayko explaining REST][rest-explained]. A good way to understand the *why* of REST, if not the *what* or *how*...
3. [Roy Fielding's thesis where REST was defined.][fielding-thesis] It's totally accessible (really)!

##### Why use REST?

- it's a good standard
- it's a helpful guide to structuring our application
- it makes our application more useful in that it is easier to use and more interoperable
- it helps us write optimize-able applications (constrain our reliance on I/O)
- it helps us to write modular, portable applications
- it allows us to use tools that rely on conventions

---

<!-- Links -->

[wikipedia-definition]: http://en.wikipedia.org/wiki/Representational_state_transfer
[rest-explained]:       http://www.looah.com/source/view/2284
[fielding-thesis]:      http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm
