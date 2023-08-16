# Learn Node.js by building a backend framework

> There’s going to be 0 dependencies for our backend framework, as well as our logging library. Everything will be done using vanilla Node.js, the hard-way (the best way to learn).

> This is still in a very early stage. It consists of almost 2-3% of the total content which it intends to cover. There will also be an pdf version of this to download, as well as a website for the documentation.

I've found that one of the best ways to get a handle on a new concept is to start from scratch. Begin with nothing, and build it up yourself. This approach lets you not only learn how it works, but also understand _why_ it works that way.

This isn't your average Node.js tutorial or guide. It's a detailed walkthrough that shows you how to create a backend framework from the ground up while getting a solid grasp of Node.js's inner workings and it’s standard library.

In this guide, we will not only build a web framework, but also focus on designing a powerful and optimized end product that is ready for use in production applications (somewhat). Our goal is to create a modular backend framework that can be easily extended with new features as needed.

We will cover topics like error handling, security, and testing to ensure that our framework is reliable and secure. We will explore different approaches to modularity and demonstrate how to create reusable components that can be shared across multiple projects. By the end of this guide, you will have a solid understanding of Node.js and it’s tough parts.

I highly recommend coding along with this guide rather than just reading it.

# Table of contents

- [What the hell is a web server any way?](/%20chapters/ch01-what-is-a-web-server-anyway)
  - [Parts of a Web Server](/%20chapters/ch01-what-is-a-web-server-anyway#parts-of-a-web-server)
  - [Navigating the World of Protocols: A Quick Overview](/%20chapters/ch01-what-is-a-web-server-anyway#navigating-the-world-of-protocols-a-quick-overview)
  - [The Relationship Between HTTP and TCP](/%20chapters/ch01-what-is-a-web-server-anyway#the-relationship-between-http-and-tcp-ensuring-reliable-web-communication)
    - [Data Integrity and Order](/%20chapters/ch01-what-is-a-web-server-anyway#1-data-integrity-and-order)
    - [Acknowledgment Mechanism](/%20chapters/ch01-what-is-a-web-server-anyway#2-acknowledgment-mechanism)
    - [Complex Interactions](/%20chapters/ch01-what-is-a-web-server-anyway#3-complex-interactions)
    - [Transmission Overhead](/%20chapters/ch01-what-is-a-web-server-anyway#4-transmission-overhead)
  - [How Web Servers Respond to Your Requests](/%20chapters/ch01-what-is-a-web-server-anyway#asking-and-getting-how-web-servers-respond-to-your-requests)
    - [The Request](/%20chapters/ch01-what-is-a-web-server-anyway#the-request)
      - [Your Request](/%20chapters/ch01-what-is-a-web-server-anyway#1-your-request)
      - [Finding the Address](/%20chapters/ch01-what-is-a-web-server-anyway#2-finding-the-address)
      - [Resolving the Address](/%20chapters/ch01-what-is-a-web-server-anyway#3-resolving-the-address)
    - [The Response](/%20chapters/ch01-what-is-a-web-server-anyway#the-response)
      - [Return Address](/%20chapters/ch01-what-is-a-web-server-anyway#1-return-address)
      - [Sending the Request](/%20chapters/ch01-what-is-a-web-server-anyway#2-sending-the-request)
      - [Preparing the Content](/%20chapters/ch01-what-is-a-web-server-anyway#3-preparing-the-content)
      - [Sending the Response](/%20chapters/ch01-what-is-a-web-server-anyway#4-sending-the-response)
      - [Enjoying the Content](/%20chapters/ch01-what-is-a-web-server-anyway#5-enjoying-the-content)
- [Your first web server with node.js](/%20chapters/ch02-your-first-nodejs-server)
  - [What exactly is node or nodejs?](/%20chapters/ch02-your-first-nodejs-server#what-exactly-is-node-or-nodejs)
  - [Your first node.js program](/%20chapters/ch02-your-first-nodejs-server#your-first-nodejs-program)
  - [How does console.log() work in Node.js?](/%20chapters/ch02-your-first-nodejs-server#how-does-consolelog-work-in-nodejs)
  - [The process Object](/%20chapters/ch02-your-first-nodejs-server#the-process-object)
  - [The stdout property of the process object](/%20chapters/ch02-your-first-nodejs-server#the-stdout-property-of-the-process-object)
- [Working with files](/%20chapters/ch03-working-with-files.md)
  - [What will the logging library do](/%20chapters/ch03-working-with-files.md#what-will-the-logging-library-do)
  - [How do you work with files anyway?](/%20chapters/ch03-working-with-files.md#how-do-you-work-with-files-anyway)
  - [Let's get back to files](/%20chapters/ch03-working-with-files.md#lets-get-back-to-files)
  - [A little more about file descriptors](/%20chapters/ch03-working-with-files.md#a-little-more-about-file-descriptors)
  - [Creating our first file](/%20chapters/ch03-working-with-files.md#creating-our-first-file)
    - [`path` argument](/%20chapters/ch03-working-with-files.md#path-argument)
    - [`flag` argument](/%20chapters/ch03-working-with-files.md#flag-argument)
    - [`mode` argument](/%20chapters/ch03-working-with-files.md#mode-argument)
  - [Reading from a file](/%20chapters/ch03-working-with-files.md#reading-from-a-file)
  - [Reading the json file](/%20chapters/ch03-working-with-files.md#reading-the-json-file)
  - [Buffers](/%20chapters/ch03-working-with-files.md#buffers)
  - [Parsing the json file](/%20chapters/ch03-working-with-files.md#parsing-the-json-file)
- [`logtar` - Our Own logging library](/%20chapters/ch04-logtar-our-logging-library.md)
  - [Initializing a new project](/%20chapters/ch04-logtar-our-logging-library.md#initialising-a-new-project)
  - [A little about `SemVer`](/%20chapters/ch04-logtar-our-logging-library.md#a-little-about-semver)
  - [Creating a LogLevel class](/%20chapters/ch04-logtar-our-logging-library.md#creating-a-loglevel-class)
  - [The Logger class](/%20chapters/ch04-logtar-our-logging-library.md#the-logger-class)
  - [Encapsulation with private fields](/%20chapters/ch04-logtar-our-logging-library.md#encapsulation-with-private-fields)
  - [The `LogConfig` class](/%20chapters/ch04-logtar-our-logging-library.md#the-logconfig-class)
  - [Design Patterns](/%20chapters/ch04-logtar-our-logging-library.md#design-patterns)
    - [The `Builder` pattern](/%20chapters/ch04-logtar-our-logging-library.md#the-builder-pattern)
    - [Using the `Builder` pattern with the `LogConfig` class](/%20chapters/ch04-logtar-our-logging-library.md#using-builder-pattern-with-the-logconfig-class)
  - [`jsdoc` comments](/%20chapters/ch04-logtar-our-logging-library.md#jsdoc-comments)
