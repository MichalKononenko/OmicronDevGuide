Core Concepts
=============

    Program testing can be used to show the presence of bugs, but never to
    show their absence!
                        - Edsger Dijkstra, "Notes on Structured Programming"

This section is a primer into development on the Omicron Project, meant to
introduce some of the concepts and tools used in this project to deliver
site functionality. Each sub-project in Omicron will obviously have its own
dependencies, and challenges unique to that project, but some common concepts
can be ironed out.

For instance, you will probably need to know

    -   How to consume and prepare a RESTful API
    -   How to work with ``git`` beyond ``git clone``
    -   Setting up Continuous Integration

HTTP REST API Services and you
------------------------------

Back in 2000, Roy Fielding's `Ph. D dissertation`_ introduced the idea that
data transfer on the World Wide Web could be boiled down to, essentially,
six design constraints. These are

    -   The service must operate on a client-server model
    -   The service must be stateless
    -   The service should be able to provide code on demand
    -   The responses from the service should be cacheable
    -   The service must provide a uniform interface to the client
    -   The service should *not* make any distinctions between being connected
        to the end user or to an intermediary.

.. _Ph. D dissertation: https://goo.gl/SSbjpX

Note that these constraints are equally satisfied when implemented with the
Omicron Project codebase or a sufficiently advanced network of carrier pigeons.
Therefore, additional constraints have been placed upon REST with the use of
HTTP.

The basics of HTTP
~~~~~~~~~~~~~~~~~~

The Hypertext Transfer Protocol (HTTP) is the bedrock of the World Wide Web,
being implemented on pretty much every web browser ever. In addition, HTTP
libraries exist for the vast majority of programming languages. A few of
them are

            =============    =============================
             **Language**         **Library**
            -------------    -----------------------------
             C                 `libcurl`_
            -------------    -----------------------------
             C++               `curlcpp`_
            -------------    -----------------------------
             Python            `requests`_
            -------------    -----------------------------
             Java              `Apache HTTP Components`_
            -------------    -----------------------------
             Javascript        `jQuery`_
            -------------    -----------------------------
             Mathematica       `URLFetch`_
            -------------    -----------------------------
             MATLAB            `Webread`_ and `Webwrite`_
            =============    =============================

.. _libcurl: http://libcurl.org/
.. _curlcpp: https://josephp91.github.io/curlcpp/
.. _requests: http://docs.python-requests.org/en/latest/
.. _Apache HTTP Components: https://hc.apache.org/
.. _jQuery: https://jquery.com/
.. _URLFetch: https://goo.gl/zv0nsX
.. _Webread: https://www.mathworks.com/help/matlab/ref/webread.html
.. _Webwrite: https://www.mathworks.com/help/matlab/ref/webwrite.html

HTTP follows a request-response pattern between a client and a server. An HTTP
request consists of
    -   The address to which the request is being sent
    -   An `HTTP method`_, stating what must be done at this address
        (for example, ``GET``).
    -   A set of request `header fields`_ that describe request metadata
    -   The request body, containing the actual data to be sent

.. _HTTP method: http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html
.. _header fields: https://en.wikipedia.org/wiki/List_of_HTTP_header_fields

The response consists of a set of header fields similar to those of the
request, the response body, and a `status code`_ that tells the client about
the status of their request (whether it completed successfully, whether it is
completing asynchronously, etc.).

.. _status code: http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html

This request-response cycle is the reason why most REST APIs are implemented
over HTTP. It's easy to have a client-server architecture when the protocol
used has client-server baked in.

JSON and JSON Schema
~~~~~~~~~~~~~~~~~~~~

All input and output parameters will be served in `Javascript Object
Notation (JSON)`_. If any metadata about JSON needs to be communicated,
`JSON Schema`_ and `JSON Hyper-schema`_ should be used to communicate it. These
are emerging standards for description of JSON object and JSON object
servers written in JSON. These two technologies are intended for fulfilling
the REST requirement for a uniform interface by using Hypermedia As The Engine
of Application State (`HATEOAS`_)

.. _Javascript Object Notation (JSON): http://json.org/
.. _JSON Schema: http://json-schema.org/
.. _JSON Hyper-schema: http://goo.gl/OY8Yee
.. _HATEOAS: https://en.wikipedia.org/wiki/HATEOAS


Git and Github
~~~~~~~~~~~~~~

