---
title: "Getting Started with GraphQL" # Title of the blog post.
date: 2020-09-26T17:40:58+08:00 # Date of post creation.
description: "In this tutorial, I'm going to show you how to get started with GraphQL. GraphQL is an awesome technology that is faster compared to your typical REST API. I am going to be using NodeJS and Express to demonstrate the power of GraphQL." # Description used for search engine.
featured: true # Sets if post is a featured post, making it appear on the sidebar. A featured post won't be listed on the sidebar if it's the current page
draft: false # Sets whether to render this page. Draft of true will not be rendered.
toc: false # Controls if a table of contents should be generated for first-level links automatically.
# menu: main
featureImage: "/default.jpg" # Sets featured image on blog post.
thumbnail: "/default.jpg" # Sets thumbnail image appearing inside card on homepage.
shareImage: "/default.jpg" # Designate a separate image for social media sharing.
codeMaxLines: 14 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
categories:
  - Tutorial
tags:
  - GraphQL
  - NodeJS
  - Javascript
---

**What is GraphQL?**

**GraphQL** is like another way to send data from server to client. I hope that you're familiar as to what a REST API is, but the essential difference(that I know of) is that in a REST API, you would need to set up a lot of endpoints like `'/'` or `'/login'` or `'/about'`. GraphQL, however, really is set up on one endpoint `'/graphql'` and requires the client to *query as to which data the client would **need***. Which is a good segue to GraphQL's most impressive feature, you can select which data gets "sent". It might be confusing, but it'll be easier once we get our hands dirty with GraphQL.

**Getting Started with NodeJS and Express**

For the purposes of this article, I'm going to stick with NodeJS. First, we need to initialize a directory as an npm thingy(i.e. initialize package.json). In your project directory... `npm init` to create a package.json file with dependencies and important wackadoo-dle's you need.

```shell
$ npm init
```

What package.json might look like:

```json
{
  "name": "graphql_practice",
  "version": "1.0.0",
  "description": "Practice with graphql",
  "main": "server.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Vincent Hong",
  "license": "ISC"
}
```

> Note: During `npm init`, I did change some values like the name, description, main entry point(index.js to server.js), and author  

Now, let's install express express-graphql and graphql as dependencies
```shell
$ npm install express express-graphql graphql
```

Now, in your **sever.js** file or your entry js file (create new file named server.js), we need to require / import the dependencies so we can actually use them in our code...
```javascript
// Require or import helper packages

const express = require('express');
const app = express();
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');
```

Let's take this step by step...

1. What is express? Well, express is essentially a NodeJS package that makes creating http endpoints super easy!
2. What is app? Well, I'm given to understand that `express` is a higher order function. Meaning it returns another function, which we named `app`.
3. What is `const { graphqlHTTP } = require('express-graphql');`? `graphqlHTTP` makes it easy to use graphql with express. you'll know more later...
4. What is `const { buildSchema } = require('graphql');`? `buildSchema` is used to make a schema that is used for GraphQL queries.
   

Now, let's look at the implementation...
```javascript
// defining schema, be careful... the first time I learned GraphQL,
// I didn't see the backticks and had errors until I figured out the problem
const schema = buildSchema(`
    type Query {
        name: String
    }
`);

// Types should be uppercase

// defining root
const root = {
    name: () => "Hello world"
}

// setup /graphql endpoint
app.use('/graphql', graphqlHTTP({
    schema: schema,
    rootValue: root,
    graphiql: true
}));
// graphiql: true means to enable graphiql which is a graphical user interface for querying graphql stuff...

// Server Listening on port 5000
app.listen(5000, () => console.log('Listening on port 5000...'));

```

After that run( **make sure to run it on the root of your project directory** ):
```shell
$ node server
```

- Go to your browser and type in `http://localhost:5000/graphql`
- Delete everything on the left side of the graphiql and type:
```
{
  name
}
```
- Start with curly braces much like a javascript object, and type in the name of what you want to query(in this case, `name`)

Response:
```
{
  "data": {
    "name": "Hello world"
  }
}
```

**Extra Resources**
- [GraphQL Docs](https://graphql.org/graphql-js/running-an-express-graphql-server/)
