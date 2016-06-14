---
layout: post
title:  "API Route Identifiers"
date:  2016-06-12 17:50:00 -0800
categories: rest api webapi route naming identifiers
---

Creating meaningful, simplistic, and long-lived routes is one of the hardest things to do when creating an API.  To get a better understanding of how to do this we will first look at what a URL is and pick apart how different parts of the URL can be used to give a consistent feel to your API.  Secondly, we discuss the ever contentious "plural vs. singular" debate.  Lastly, we'll go over a few minor items of interest, status codes, api versioning, and long lived URLs, that have found their way into this article.

## What is a URL?

A [URL][wiki-url], uniform resource locator, is an **identifier** that provides all the information necessary to retrieve a resource.  The important bit is when you read **identifier**.  A URL is a jumble of text that identifies a resource sitting on a server.  The resource could be a folder or a file sitting on a server or it could be a dynamic collection of items or a single item.  The URL represents something just like your name represents you!

Let's look at the syntax of a URL which is actually a more specific variant of a [URI][wiki-uri] and conforms to the syntax of a URI as seen below.

	scheme:[//[user:password@]host[:port]][/]path[?query][#fragment]

Here's a pretty normal URL that we've seen in the wild:

	https://search.yahoo.com/search?p=URL

where

* "https"is the scheme.
* "search.yahoo.com" is the host.
* "search" is the path.
* "p=URL" is the query.

Let's focus on the path and query portions of a URL for the remainder of this article and we'll hone in on URLs with respect to a web api.  Enough with this generic URL description crud!  

### Path

The path generally looks like the path to a file on your local computer, like: users/mwooolfe/documents/resume.txt.  The path does not have to map exactly to a file system on the server and most often does not.

Talk about how to name an api and how to break it apart correctly
* /customer returns the set of all customers
* /customer/5 returns customer with id of 5
* /customer/5/email would return the email address of customer with id 5.

Pull a reference for the customer/5/email part and discuss how this is all really playing with the query string to change filters into path elements.

### Query parameters

Discuss how filters should be part of the query string, but not part of the path...but then dive into how that is a sticky subject as you have shit like customer/5/email that is apparently acceptable, but not a filter.


## Plural vs. Singular

Argue that we use singular in DB tables and singular in class names.  Also, give examples of why plural sucks in english and there are no standard forms (login, status).

Here's two pretty good discussions i've found
* http://stackoverflow.com/questions/6845772/rest-uri-convention-singular-or-plural-name-of-resource-while-creating-it
* http://stackoverflow.com/questions/338156/table-naming-dilemma-singular-vs-plural-names/5841297

## Status Codes

Talk about using the correct status code as a response.  If /customer/5 doesn't exist then return a 404 Not Found.  Don't return a 200 OK with a JSON message that indicates failure.  I'm all good with JSON messages that indicate failure and expand on the issue that occurred, but don't break the cacheable architectural constraint just so you can feel good about returned a 200 OK like you actually succeeded to find the customer.

https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html

## API versioning

API versioning shouldn't be present in the URL (identifier).  Add it as a query parameter or body parameter.

## Long lived URLs



## Conclusion

In the end, this is what makes sense to me.  You should write your APIs with what makes sense to both you and your partner...because that's who you're writing them for anyway, right?

[wiki-url]: https://en.wikipedia.org/wiki/Uniform_Resource_Locator		"URL"
[wiki-url]: https://en.wikipedia.org/wiki/Uniform_Resource_Identifier	"URI"