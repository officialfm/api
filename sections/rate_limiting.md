# Rate Limiting

### Anonymous calls

If you request the Official.fm API as an anonymous requester, you could only make a limited number of calls in a given hour. This rate limit is applied to the IP that the request is coming from.

If you reach the hourly rate limit, you will receive HTTP 429 response code.

### Authenticated calls

By registering your application on the [developers page](http://official.fm/developers), you will allow to make more API calls. On our side, we monitor all registered applications and adjust their rate limits.

If your application is reaching the rate limit, it will receive HTTP 429 response code.

### Questions?

You're writing an application which will make a lot of official.fm API requests and you want to be sure you won't be rate limited at launch? Contacting us at [api@official.fm](mailto:api@official.fm).