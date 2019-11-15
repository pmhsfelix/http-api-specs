# Introduction

A collection of RFCs and other specifications useful when designing and implementing HTTP APIs.

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

### [IANA Link Relation registry](http://www.iana.org/assignments/link-relations/link-relations.xhtml) 

The IANA registry with all the standard link relations.
This is the place to go when selecting or creating link relations.

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

*The* OAuth 2.0 framework main specification, describing how a client application obtains access tokens to access a HTTP API, using one of the four standard flows: Authorization Code Grant, Implicit, Resource Owner Password Credentials, and Client Credentials.

### [The OAuth 2.0 Authorization Framework: Bearer Token Usage](https://tools.ietf.org/html/rfc6750)

From the abstract
> This specification describes how to use bearer tokens in HTTP
   requests to access OAuth 2.0 protected resources

A rather short specification defined the proper way to attach a bearer token to a HTTP request message.

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
