## JSON Simple Syndication

**RSS-JSON**, a working title for a Really Simple Syndication spec using JSON.

### Goals

An easy way to syndicate content, RSS-style, while attaching as much extra data as you want.

In other words, it should be just as simple as normal RSS to make a universal "list of content" with a title/link/description/time, but possible to go much further in applications that specialize in one or more types of content.

An item might look something like:

```json
{
  "title": "An Insightful Blog Post",
  "description": "The beginning of my post is as follows...",
  "url": "https://someonegreat.com/insightful-blog-post",
  "published_at": "2014-04-10T19:00:00Z",

  "source": "someonegreat.com",
  "type": "article",
  "id": "insightful-blog-post",

  "data": {
    "home": "https://someonegreat.com",
    "author": {
      "email": "someone@someonegreat.com",
      "twitter": "https://twitter.com/someonegreat"
    },
    "tags": ["insight", "please post me to hacker news"]
  }
}
```

but also something like:

```json
{
  "title": "McCutcheon et al. v. Federal Election Commission",
  "description": "",
  "url": "http://www.supremecourt.gov/opinions/13pdf/12-536_e1pf.pdf",
  "published_at": "2014-04-10T19:00:00Z",

  "source": "supremecourt.gov",
  "type": "opinion",
  "id": "347-us-483",

  "data": {
    "citation": "347 U.S. 483",
    "court": "scotus",
    "decided": "5-4"
  }
}
```

In the above examples, there are enough top-level fields to support typical RSS-like uses, but anyone interested in processing specific kinds of documents can dig into the `data` object and go for it.

`data` is fair game for anyone. Create sub-specs for your use cases, start shipping them places. Your community wants to put JSON-LD in there for their work? Sounds great.

This is what Twitter was once going for with their beautiful (and now dead) [proposal for Annotations](http://www.slideshare.net/raffikrikorian/twitter-api-annotations).

### Avoiding URLs as GUIDs

The above examples avoid URLs as unique IDs. Instead, they prefer combining keys.

For example, `id`, `type`, and `source` could be reliably unique when combined. If you need to serialize that into an ID somewhere in your system, go for it.

Reasons to avoid URLs:

* The document's URL can change without disturbing its ID.
* Separate fields favor short, slug-like strings. URLs are large and difficult to remember and type.
* A single ID would just repeat the constituent parts anyway, but joined together using some arbitrary delimiter. Instead, let JSON be the delimiter.

There are also drawbacks, chiefly forcing everyone to serialize an ID from constituent parts.

### Join the discussion

Everything's up for debate - this is a proposal. Come read and join [the main discussion thread](https://github.com/konklone/rss-json/issues/1).
