# edison-microservice - branch 1.2.x

Collection of independent libraries on top of Spring Boot to provide a faster setup of jvm microservices.

> "I never did anything by accident, nor did any of my inventions come by accident; they came by work." - Thomas Edison


## Status

[![build](https://github.com/otto-de/edison-microservice/workflows/Build/badge.svg?branch=1.2.x)](https://github.com/otto-de/edison-microservice/actions?query=workflow%3ABuild+branch%3A1.2.x) 
[![codecov](https://codecov.io/gh/otto-de/edison-microservice/branch/1.2.x/graph/badge.svg)](https://codecov.io/gh/otto-de/edison-microservice)
[![release](https://maven-badges.herokuapp.com/maven-central/de.otto.edison/edison-core/badge.svg)](https://maven-badges.herokuapp.com/maven-central/de.otto.edison/edison-core)
[![license](https://img.shields.io/github/license/otto-de/edison-microservice.svg)](./LICENSE)

Have a look at the [release notes](CHANGELOG.md) for details about updates and changes.

## About

This project contains a number of independent libraries on top of Spring Boot to provide a faster setup of jvm microservices.
The libraries are used in different projects at OTTO.
It's purpose is to provide a common implementation for cross-cutting requirements like:

* Health checks that are used to tell the load balancer or mesos platform whether or not a service is healthy.
* A [status page/document](https://github.com/otto-de/edison-microservice/tree/master/edison-core) that is used to give information about the current state of the service. Status information also include details about sub-components, background jobs like imports, and so on.
* A simple job handling library that is used to run asynchronous background jobs, which for example can be used to run data imports from other systems.
* An optional MongoDB-based implementation of a JobRepository
* Support for MongoDB-based repositories in case you do not like Spring Data
* Reporting of metrics to Graphite
* Support for [Caffeine caches](https://github.com/otto-de/edison-microservice/tree/master/edison-cache)
* Support for feature toggles based on [Togglz](https://www.togglz.org/)

... plus all the features of [Spring Boot](http://projects.spring.io/spring-boot/).


## Future Releases aka Roadmap

[Semantic Versioning v2.0.0](http://semver.org/spec/v2.0.0.html) is used to specify the version numbers.

This project maintains its roadmap with [issues](https://github.com/otto-de/edison-microservice/issues) and [milestones](https://github.com/otto-de/edison-microservice/milestones).

**[1.0.0](https://github.com/otto-de/edison-microservice/milestone/1)**: Edison Microservices for Spring Boot 1.4 &#10004;

**[1.1.0](https://github.com/otto-de/edison-microservice/milestone/2)**: Edison Microservices for Spring Boot 1.5 &#10004;

**[2.0.0](https://github.com/otto-de/edison-microservice/milestone/3)**: Edison Microservices for Spring Boot 2.0


## Documentation

Edison Modules:
* [`edison-core`](edison-core/README.md): Main library of Edison microservices.
* [`edison-cache`](edison-cache/README.md): Optional support for Caffeine caches in Edison.
* [`edison-jobs`](edison-jobs/README.md): Optional module providing a simple job library.
* [`edison-mongo`](edison-mongo/README.md): Auto-configuration for MongoDB repositories plus implementation of MongoJobRepository and
 Togglz StateRepository.
* [`edison-dynamodb`](edison-dynamodb/README.md): Auto-configuration for DynamoDB repositories plus implementation of DynamoJobRepository and
 Togglz StateRepository.
* [`edison-oauth`](edison-oauth/README.md): Auto-configuration for OAuth Public Key repositories with autofetching and a simple JWT Token Validation.
* [`edison-togglz`](edison-togglz/README.md): Optional support for feature toggles for Edison microservices based on [Togglz](https://www.togglz.org/).
* `edison-testsupport`: Test support for feature toggles plus utilities.
* [`edison-validation`](edison-validation/README.md): Optional module for validation in Spring with a specific response format.

Examples:
* [`example-status`](examples/example-status): Service only relying on `edison-core` to show the usage of health and status features. 
* [`example-metrics`](examples/example-metrics): Service that is using edison-core metrics.
* [`example-jobs`](examples/example-jobs): Edison service using edison-jobs to run background tasks. 
* [`example-togglz`](examples/example-togglz): Example using `edison-togglz´ to implement feature toggles.
* [`example-togglz-mongo`](examples/example-togglz-mongo): Same `edison-toggz`, but with a MongoDB configuration to auto-configure persistence of feature toggles.


## Setup

Make sure you have Java 1.8 and gradle 3.x installed on your computer.

### Testing

Test and create coverage report

    gradle check

### Dependency Update

Determine possible dependency updates

    gradle dependencyUpdates -Drevision=release

### Publishing

Publish new releases

    gradle uploadArchives


## Examples

There are a few examples that may help you to start your first microservice based
on Edison and Spring Boot. Because Spring Boot itself has some complexity, it is
recommended to first read it's documentation before starting with Edison.

The examples can be started with gradle:

    gradle examples:example-status:bootRun
    gradle examples:example-metrics:bootRun
    gradle examples:example-jobs:bootRun
    gradle examples:example-togglz:bootRun
    gradle examples:example-togglz-mongo:bootRun

Open in your browser [http://localhost:8080/](http://localhost:8080/)

*Note:* Every example is configured to use port 8080, so make sure to run only one example at a time or to reconfigure
the ports.


## Contributing

Have a look at our [contribution guidelines](CONTRIBUTING.md).
