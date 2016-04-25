---
title: HTTP API Specs
layout: default
---

# Introduction

A collection of RFCs and other specifications, useful when designing and implementing HTTP APIs.

# Summary

Area     | Spec 
---------|----------
HTTP                             | [Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content](#hypertext-transfer-protocol-http11-semantics-and-contenthttpstoolsietforghtmlrfc7231)
Links                            | [Web Linking](#web-linkinghttpstoolsietforghtmlrfc5988)
Links                            | [URI Template](#uri-templatehttpstoolsietforghtmlrfc6570)
Links                            | [IANA Link Relation registry](#iana-link-relation-registryhttpwwwianaorgassignmentslink-relationslink-relationsxhtml)
Generic Media Types              | [JSON Hypertext Application Language](#json-hypertext-application-languagehttpstoolsietforghtmldraft-kelly-json-hal-07)
Generic Media Types              | [Siren](#sirenhttpsgithubcomkevinswibersiren)
Generic Media Types              | [Collection+JSON](#collectionjsonhttpamundsencommedia-typescollection)
Other Media Types                | [Problem Details for HTTP APIs](#problem-details-for-http-apishttpstoolsietforghtmlrfc7807)
Other Media Types                | [Home Documents for HTTP APIs](#home-documents-for-http-apishttpstoolsietforghtmldraft-nottingham-json-home-03)
Semantics                        | [The ‘profile’ Link Relation Type](#the-profile-link-relation-typehttpstoolsietforghtmlrfc6906)
Negotiation                      | [Prefer Header for HTTP](#prefer-header-for-httphttpstoolsietforghtmlrfc7240)
Caching                          | [HTTP Cache-Control Extensions for Stale Content](#http-cache-control-extensions-for-stale-contenthttpstoolsietforghtmlrfc5861")
Security                         | [Hypertext Transfer Protocol (HTTP/1.1): Authentication](#hypertext-transfer-protocol-http11-authenticationhttpstoolsietforghtmlrfc7235)
Security                         | [The OAuth 2.0 Authorization Framework](#the-oauth-20-authorization-frameworkhttpstoolsietforghtmlrfc6749)
Security                         | [The OAuth 2.0 Authorization Framework: Bearer Token Usage](#the-oauth-20-authorization-framework-bearer-token-usagehttpstoolsietforghtmlrfc6750)
Security                         | [OpenID Connect Core 1.0](#openid-connect-core-10httpopenidnetspecsopenid-connect-core-10html)
Security                         | [IANA HTTP Authentication Schemes registry](#iana-http-authentication-schemes-registryhttpwwwianaorgassignmentshttp-authschemeshttp-authschemesxhtml)
Syntax                           | [Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing](hypertext-transfer-protocol-http11-message-syntax-and-routinghttpstoolsietforghtmlrfc7230)
Syntax                           | [Uniform Resource Identifier (URI): Generic Syntax](uniform-resource-identifier-uri-generic-syntaxhttpstoolsietforghtmlrfc3986)


# Specifications

## The HTTP protocol

### [Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content](https://tools.ietf.org/html/rfc7231)

From the abstract

> The Hypertext Transfer Protocol (HTTP) is a stateless application-
   level protocol for distributed, collaborative, hypertext information
   systems.  This document **defines the semantics of HTTP/1.1 messages,
   as expressed by request methods, request header fields, response
   status codes, and response header fields, along with the payload of
   messages (metadata and body content) and mechanisms for content
   negotiation**.

My primary source of information for the semantics of the HTTP main components, such as request methods, status codes and headers. 



## Links

### [Web Linking](https://tools.ietf.org/html/rfc5988)

From the abstract

> This document specifies **relation types for Web links**, and defines a
   registry for them.  It also defines the use of such links in HTTP
   headers with the **Link header field**.

This specification defines:

* what is a link and what are its constituents
* a set of standard link relations
* the `Link` header to add links at the HTTP message level

### [URI Template](https://tools.ietf.org/html/rfc6570)

From the abstract

> A URI Template is a compact sequence of characters for describing a
   range of Uniform Resource Identifiers through variable expansion.
   *This specification defines the URI Template syntax and the process
   for expanding a URI Template into a URI reference*, along with
   guidelines for the use of URI Templates on the Internet.

Defines a standard syntax to represent a URI template, which is a descriptions of a range of Uniform Resource Identifiers through variable expansion.
Very useful when the server needs to provide the client with a recipe to build URIs instead of a absolute URI.
An template example is `https://api.github.com/users/{user}`, which produces `https://api.github.com/users/pmhsfelix` when the varible `user` is replaced with the value `pmhsfelix`.

### [IANA Link Relation registry](http://www.iana.org/assignments/link-relations/link-relations.xhtml) 

The IANA registry with all the standard link relations.
This is the place to go when selecting or creating link relations.

## Generic media types

### [JSON Hypertext Application Language](https://tools.ietf.org/html/draft-kelly-json-hal-07)

From the abstract

> This document proposes a media type for representing resources and
   their relations with hyperlinks.

One of the first JSON based media types with hypermedia support.
Basic support for links and embedded representations.
Used by the [Amazon API Gateway configuration API](https://docs.aws.amazon.com/apigateway/api-reference/). 


### [Siren](https://github.com/kevinswiber/siren)

From the introduction

> Siren is a hypermedia specification for representing entities. As HTML is used for visually representing documents on a Web site, Siren is a specification for presenting entities via a Web API. Siren offers structures to **communicate information about entities, actions for executing state transitions, and links for client navigation**.

Another JSON based media type with hypermedia support.
Compared with HAL, it introduces the concepts of *actions* (non safe links) and of *classes*.
Used by the [Zetta IoT platform](http://www.zettajs.org).

### [Collection+JSON](http://amundsen.com/media-types/collection/)

From the description

> Collection+JSON is a JSON-based read/write hypermedia-type designed to support management and querying of simple collections.

A more specialized hypermedia enabled media type, designed specifically to manage collections.

## Media types for specific usages

### [Problem Details for HTTP APIs](https://tools.ietf.org/html/rfc7807)

From the abstract

> This document defines a "problem detail" as a way to carry machine-
   readable details of errors in a HTTP response to avoid the need to
   define new error response formats for HTTP APIs.

A media type to use when a status code is not enough to represent all the error information.
I typically use it to add domain specific information to error HTTP response messages, using the `type` field.

### [Home Documents for HTTP APIs](https://tools.ietf.org/html/draft-nottingham-json-home-03)

From the abstract

> This document proposes a "home document" format for non-browser HTTP clients.

Defines a format for API home documents - the API entry point, containing links to relevant resources.
An example of such a document is [https://api.github.com](https://api.github.com), which does not use this specification.

Includes the definition of two concepts that may be used in other contexts, other than a home document:

* `href-vars` as a way to provide additional information about URI template variables.

* `hints` that provide advisory information about a resource, prior to any interaction with it. An example is `auth-req` that hits that the resource require authentication.

## Semantics

### [The 'profile' Link Relation Type](https://tools.ietf.org/html/rfc6906)

From the abstract

> This specification defines the 'profile' link relation type that
   allows resource representations to indicate that they are following
   one or more profiles.  A profile is defined not to alter the
   semantics of the resource representation itself, but to **allow clients
   to learn about additional semantics (constraints, conventions,
   extensions) that are associated with the resource representation, in
   addition to those defined by the media type and possibly other
   mechanisms.**

Useful to communicate the representation semantics beyond what is provided by the media type alone. Avoid the creation of specific media type identifiers.

For instance, the following response informs that the HMTL based representation includes elements that should be interpreted according to the [hCard 1.0](http://microformats.org/wiki/hcard) format.

~~~
HTTP/1.1 200 OK
Content-Type: text/html
Link: <http://microformats.org/profile/hcard>; rel="profile"

~~~

The next excerpt includes the `tel`, `type` and `value` HTML classes, which should be interpreted according to the hCard semantics.

~~~
<span class="tel">
 <span class="type">home</span>:
 <span class="value">+1.415.555.1212</span>
</span>
~~~

## Negotiation

### [Prefer Header for HTTP](https://tools.ietf.org/html/rfc7240)

From the abstract

> This specification defines an HTTP header field that can be used by a client to request that certain behaviors be employed by a server while processing a request.

Define a way for the client to influence how a server handles a request, by stating a set of preferences such as 

* `response-async` - preference for the server to respond immediately with a 202 and perform the remaining work asynchronously.
* `return=representation | minimal` - preference for a full representation versus a minimal representation for a resource.

IANA manages a [registry](http://www.iana.org/assignments/http-parameters/http-parameters.xhtml#preferences) for these preferences.

## Caching

### [HTTP Cache-Control Extensions for Stale Content](https://tools.ietf.org/html/rfc5861)

From the abstract

> This document defines two independent HTTP Cache-Control extensions
   that allow control over the use of stale responses by caches.

This RFC defines two new cache control directives that allow the use of stale content by caches:

* `stale-if-error` allows a cache intermediary to return stale content if an error occurs when revalidating this content. 
By returning stale content instead of an error, it helps to increase perceived availability.

* `stale-while-revalidate` allow a cache intermediary to return stale content immediately, while at the same time triggers an asynchronous revalidation. 
By returning stale content immediately, instead of waiting for the revalidation result, it helps to reduce perceived latency.

In addition, the `Warning` header can be used to inform the client that stale content is being returned: [https://tools.ietf.org/html/rfc7234#section-5.5.1](https://tools.ietf.org/html/rfc7234#section-5.5.1).

## Security

### [Hypertext Transfer Protocol (HTTP/1.1): Authentication](https://tools.ietf.org/html/rfc7235)

From the abstract

> This document defines the HTTP Authentication framework.

My primary source of information for the HTTP authentication and authorization elements, such as the `WWW-Authenticate` and `Authorization` headers as well as the `401` and `403` status codes.

### [The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)

From the abstract

> The OAuth 2.0 authorization framework **enables a third-party
   application to obtain limited access to an HTTP service, either on
   behalf of a resource owner by orchestrating an approval interaction
   between the resource owner and the HTTP service, or by allowing the
   third-party application to obtain access on its own behalf**

The OAuth 2.0 framework main specification, describing how a client application obtains access tokens to access a HTTP API, using one of the four standard flows: Authorization Code Grant, Implicit, Resource Owner Password Credentials, and Client Credentials.

### [The OAuth 2.0 Authorization Framework: Bearer Token Usage](https://tools.ietf.org/html/rfc6750)

From the abstract

> This specification describes how to use bearer tokens in HTTP
   requests to access OAuth 2.0 protected resources

A very short specification defining the proper way to attach a bearer token to a HTTP request message.

### [OpenID Connect Core 1.0](http://openid.net/specs/openid-connect-core-1_0.html)

From the abstract

> OpenID Connect 1.0 is a simple identity layer on top of the OAuth 2.0 protocol

OpenID Connect extends the OAuth 2.0 protocol to also handle authentication related tasks.

### [IANA HTTP Authentication Schemes registry](http://www.iana.org/assignments/http-authschemes/http-authschemes.xhtml)

The IANA registry all all the standard authentication/authorization schemes, namely: `Basic` and `Bearer`.

## Syntax

### [Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing](https://tools.ietf.org/html/rfc7230)

From the abstract

> This document provides an overview of HTTP architecture and
   its associated terminology, defines the "http" and "https" Uniform
   Resource Identifier (URI) schemes, **defines the HTTP/1.1 message
   syntax and parsing requirements**, and describes related security
   concerns for implementations

Useful for understanding syntax aspects, such as header encodings.

### [Uniform Resource Identifier (URI): Generic Syntax](https://tools.ietf.org/html/rfc3986)

From the abstract

> *This specification defines the generic URI syntax* and a process for
   resolving URI references that might be in relative form, along with
   guidelines and security considerations for the use of URIs on the
   Internet.

Useful when handling with URI syntax issues, namely reserved characters and encoding.
