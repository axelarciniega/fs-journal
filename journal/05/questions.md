# Intro to Server side concerns with JavaScript
01. What do the letters of the acronym `CRUD` stand for?

  > The acronym CRUD stands for create, read, update, and delete

02. Each action that `CRUD` represents maps to an HTTP request. What HTTP request does each `CRUD` action correspond to?

  > Each of the crud action have different actions, create corresponds to POST, read corresponds to GET, update corresponds to PUT, and Delete corresponds to DELETE

03. What does `ORM` stand for? Which `ORM` do we use when interacting with MongoDB

  > ORM stands for object relational mapping, the ORM that we use when interacting with MongoDB mongoose

04. Which two `HTTP` request types include a body?

  > The two HTTP request types that include a body are POST and PUT

05. In a/an _______ coding model, when you call a function, it returns only when the action has finished and stops your program for the time the action takes. Likewise in a/an _______ coding model, multiple things are allowed to happen at one time. When you perform an action, your program continues to run.  Fill in the blanks.

  > 1. synchronous
    2. asynchronous

06. What are the three types of data relationships? Provide an example of each.

  > The three types of data relationships are 
  one-to-one: Where an author lives at a single address and an address only contains a single author
  one-to-many: Where a Blog might have many Comments but a comment is only related to a single Blog
  many-to-many: A book that was written by many authors. And at the same time an author may have written many books

07. What is middleware?

  > Middleware is a piece of software that acts as an intermediary between different components or layers of a system in this case it allows for them to communicate and perform tasks

08. The ______ pipeline delivers information from the client while the ______ pipeline returns it. Fill in the blanks. 

  > 1.Request
    2. Response

09. Demonstrate the pattern that is used to include a request query with the client's `HTTP` request providing the property `tag` and the value `winter`.

  > api/seasons?tag=winter

10. What is a ***virtual property***?

  > A visual property is a property that is associated with an object. For example a persons first and last name
