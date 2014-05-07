## JSON Simple Syndication

**JSS**, a working title for a JSON Simple Syndication spec.

### Goals

An easy way to syndicate content, RSS-style, while attaching as much extra data as you want.

In other words, it should be just as simple as normal RSS to make a universal "list of content" with a title/link/description/time, but possible to go much further in applications that specialize in one or more types of content.

In the below example, there are enough generic fields to support typical RSS-like uses, but anyone interested in processing specific kinds of documents has the original data in its full fidelity.

In other words, JSS is something you can "attach" to your existing JSON data streams. It's all upside.

### Example

A **channel** could be specified as a top-level `@channel` key that offers some channel metadata, and a path that points to an array of **items**:

```
{
  "results": [
    {
      ...
    }
  ],
  "@channel": {
    "items": "results",
    "name": "Inspector General Reports API",
    "link": "https://sunlightlabs.github.io/congress/"
  }
}
```

An **item** inside the **items** array might be specified by attaching an `@item` field to each one with RSS-like fields for `title`, `description`, etc.:

```json
{
  "agency_name": "Department of Homeland Security",
  "file_type": "pdf",
  "inspector_url": "http://www.oig.dhs.gov",
  "published_on": "2014-04-01",
  "report_id": "OIG-14-60",
  "title": "Management Letter for the FY 2013 DHS Financial Statements and Internal Control over Financial Reporting Audit",
  "type": "report",
  "url": "http://www.oig.dhs.gov/assets/Mgmt/2014/OIG_14-60_Mar14.pdf",

  "@item": {
    "id": "OIG-14-60",
    "title": "Management Letter for the FY 2013 DHS Financial Statements and Internal Control over Financial Reporting Audit",
    "description": "A report from the DHS inspector general.",
    "link": "http://www.oig.dhs.gov/assets/Mgmt/2014/OIG_14-60_Mar14.pdf",
    "published": "2014-04-01"
  }
}
```


### Join the discussion

Everything's up for debate - this is a proposal. Come read and join [the main discussion thread](https://github.com/konklone/jss/issues/10).
