# Rate Limiting

### Anonymous calls

If you request the Official.fm API as an anonymous requester, you can only make a limited number of calls per hour. This rate limit is applied to the IP where the request originates.

If you reach the hourly rate limit, you will receive HTTP 429 response code.

### Authenticated calls

By registering your application on the [developers page](http://official.fm/developers), you will be able to make more API calls. On our side, we monitor all registered applications and adjust their rate limits.

If your application reaches the rate limit, it will receive HTTP 429 response code.

### Questions?

If you're writing an application that will make a large number of Official.fm API requests and you want to be sure you won't be rate limited when you launch, contact us at [api@official.fm](mailto:api@official.fm).