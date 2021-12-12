## Inspiration

Large projects are often difficult to manage, with lots of issues and PRs to review. Some issues are often user specific, which don't require the attention of project managers and can be resolved by doing some online research or referring some websites/blogs. The bot takes this responsibility from the project managers.

## What it does

The bot shares links of various websites, when triggered with a certain query with the required keywords. It also requires an integer, the number of results to return.

## How to use it

An example query like `!help Cloud Native Hackathon 5` will trigger the bot. The bot checks if the issue comment starts with `!help` and ends with an `int`, the number of results.

## How we built it

After installation, the bot configures webhooks on the repositories selected by the user. When the user comments a certain query, like the example above, it will trigger the webhook, which sends the request to a NGROK endpoint (for testing purposes), where a flask server is running. The request is processed and formatted. Google API is used to fetch the results, specifing the query (here `Cloud Native Hackathon`), along with an integer (`5` here). The links are sent in a POST request to the GitHub API, authenticated via the bot, which the shares the links in a issue comment.

## Challenges we ran into

Google API can process and send any number of results. So, if the user does not specify the number of results to return, then the API will keep on scraping the results, and will not stop. So we have specified a strict format to use the bot, with max number of results as 9.

## Accomplishments that we're proud of

The project managers had to manually search the web to find relevant websites which might help in fixing the issue. The bot will save quite some time in doing this for them.

## What we learned

We learned how the use the GitHub API, how the webhooks work, and learned how to manage servers.

## What's next for Kronos

We are yet to add site specific search in Kronos. This will help to scrap several web pages from the same website. The limit on the max number of results will be changed in the near future, with an optimised solution. We are also planning to implement Open AI into the bot, which will be useful for sharing frequently used code snippets in issues.