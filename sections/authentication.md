# Authentication

## Read-only, "anonymous access"

### Accessible resources

This level of authentication is similar to trying to scrape data off the site, only with a nice RESTful interface!

It allows you to access all the public data visible through the front-end, including project information, playlists and tracks.

### Authentication method

#### Keyless

You can make a reasonable number of requests without using a key at all (this is useful for development).

#### With an application key

Registering your application has one big advantage: rate limitation for requests is less severe than keyless requests.

When registering your application, a unique `application key` is generated for your application.

You can use this api_key as a parameter like here:

http://api.official.fm/greeting?api_key=abcdefghijkl&api_version=2

```javascript
{
  'greeting':  'Hi there! You are authenticated for application key access.'
}
```

## Read-write, "acting as a user"

Coming soon