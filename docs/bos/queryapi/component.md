---
id: bos-components
title: Components handling Historical data
sidebar_label: Components & Historical data
---

Building components that handle historical blockchain data require dedicated solutions that manage the data and reduce the latency of requests, as it's not possible to scan the whole blockchain when a user makes a request.

A simple solution for developers building on NEAR BOS is using [QueryAPI](intro.md), a fully managed solution to build indexer functions, extract on-chain data, store it in a database, and be able to query it using GraphQL endpoints.

## QueryAPI

:::tip
Learn more about QueryAPI in this [QueryAPI Overview](intro.md) article.
:::

#### Tutorials

For a technical implementation deep-dive, check these QueryAPI tutorials:

  - [Posts Indexer tutorial](../tutorial/indexer-tutorials/posts-indexer.md): this indexer creates a new row in a pre-defined database for every new BOS post found on the blockchain.
  - [Hype Indexer tutorial](../tutorial/indexer-tutorials/hype-indexer.md): this indexer creates a new row in a pre-defined database for every new BOS post or comment found on the blockchain that contains either `PEPE` or `DOGE` in the contents.
  - [BOS Feed Indexer tutorial](../tutorial/indexer-tutorials/feed-indexer.md): this indexer keeps track of new posts, comments, and likes on BOS, so a social feed can be rendered quickly.

## GraphQL queries 

Using [QueryAPI's GraphiQL](index-function.md#mutations-in-graphql) tab, you can access the GraphiQL Explorer that provides a user friendly GraphQL playground, where you can view and create queries and mutations based on the DB schema that you defined for the indexer.

![QueryAPI Indexer Dashboard](/docs/assets/QAPIgraphiql.png)

You can easily set some fields and select the returning data
that you want, and the tool will build a query on the mutation panel on the right.
Then you can copy the resulting query, either in your JavaScript code so that you pass actual
data manually, or you pass in the mutation data object as a second parameter.

For example, if you go and add a new mutation, click <kbd>+</kbd>, then you can do a bunch of actions here, such as creating, deleting, or inserting posts into your table.

![Playground](/docs/assets/QAPIScreen.gif)

If you want to test your mutation, using [Debug Mode](index-function.md#local-debug-mode) you can add a specific
block to the list, and then play it to see how it works. 
Based on the indexer logic you defined, you'll get a call to the GraphQL mutation with the object
and data passed into it.

:::tip Video Walkthrough

**Tip:** watch the video on how to [create mutations in GraphQL](https://www.youtube.com/watch?v=VwO6spk8D58&t=781s).

:::

## Generate a BOS component using Playground

Creating a BOS component from a GraphQL query is simple when using QueryAPI's GraphQL Playground. Just follow these steps:

- go to the GraphiQL tab
- select the query that you want to use
- click on the <kbd>Show GraphiQL Code Exporter</kbd> button
- get some default code here, copy it,
- go to the BOS sandbox, paste it.


This will set up some boilerplate code to execute the GraphQL query, add the query that you had
in your playground and then call that query, extract the data and render it using the
render data function.

Once you have the BOS component code, you can test it out by going to [the sandbox](https://near.org/sandbox),
pasting the generated code, and then selecting <kbd>Component Preview</kbd>.
Next, you can create a nice UI over this boilerplate code, and publish your new BOS component.

### Component Examples

- [Activity Feed widget](https://near.org/near/widget/ComponentDetailsPage?src=roshaan.near/widget/user-activity-feed&tab=source) running on [near.org](https://near.org)

<!--
- Example of BOS component using BigQuery
-->
