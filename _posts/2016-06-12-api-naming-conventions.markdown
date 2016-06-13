---
layout: post
title:  "API Naming"
date:   2016-06-12 17:50:00 -0800
categories: api webapi naming identifiers
---

Quick overview

## URL/URI - Identifier

URLs are identifiers and they should be long lived identifiers.

## Path

Talk about how to name an api and how to break it apart correctly
* /customer returns the set of all customers
* /customer/5 returns customer with id of 5
* /customer/5/email would return the email address of customer with id 5.

Pull a reference for the customer/5/email part and discuss how this is all really playing with the query string to change filters into path elements.

## Query parameters

Discuss how filters should be part of the query string, but not part of the path...but then dive into how that is a sticky subject as you have shit like customer/5/email that is apparently acceptable, but not a filter.

## Status Codes

Talk about using the correct status code as a response.  If /customer/5 doesn't exist then return a 404 Not Found.  Don't return a 200 OK with a JSON message that indicates failure.  I'm all good with JSON messages that indicate failure and expand on the issue that occurred, but don't break the cacheable architectural constraint just so you can feel good about returned a 200 OK like you actually succeeded to find the customer.

https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html

## Naming conventions (Singular versus Plural)

Argue that we use singular in DB tables and singular in class names.  Also, give examples of why plural sucks in english and there are no standard forms (login, status).

Here's two pretty good discussions i've found
* http://stackoverflow.com/questions/6845772/rest-uri-convention-singular-or-plural-name-of-resource-while-creating-it
* http://stackoverflow.com/questions/338156/table-naming-dilemma-singular-vs-plural-names/5841297

## API versioning

API versioning shouldn't be present in the URL (identifier).  Add it as a query parameter or body parameter.

### Conclusion

In the end, this is what makes sense to me.  You should write your APIs with what makes sense to both you and your partner...because that's who you're writing them for anyway, right?