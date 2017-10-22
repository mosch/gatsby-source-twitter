# gatsby-source-twitter

Source plugin for pulling data into Gatsby from Twitter Search API.

## How to use
```javascript
// In your gatsby-config.js
module.exports = {
  plugins: [
    {
        resolve: `gatsby-source-twitter`,
        options: {           
            q: `@wesbos`,    
            credentials: {
                consumer_key: "INSERT_HERE_YOUR_CONSUMER_KEY",
                consumer_secret: "INSERT_HERE_YOUR_CONSUMER_SECRETE",
                bearer_token: "INSERT_HERE_YOUR_BEARER_TOKEN"
            }
        }
    }
  ],
}
```

## Plugin options

* **q**: A search query. Reference to [Twitter Search Tweets API](https://developer.twitter.com/en/docs/tweets/search/api-reference/get-search-tweets)
* **count**: Number of tweet *(default 100)*
* **credential**: You have to create an [App on Twitter](https://apps.twitter.com/) and creating a bearer token following this [instructions](https://developer.twitter.com/en/docs/basics/authentication/api-reference/token) using your consumer key and consumer secret

## How to query your Tweets data using GraphQL

Below is a sample query for fetching all Tweets nodes. 

```graphql
query PageQuery {
    allTweet {
        edges {
            node {
                created_at
                text
                user {
                    name
                }
            }
        }
    }
}
```