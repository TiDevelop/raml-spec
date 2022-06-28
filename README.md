# The RESTful API Modeling Language (RAML) Spec

[![Build Status](https://travis-ci.org/raml-org/raml-spec.svg?branch=master)](https://travis-ci.org/raml-org/raml-spec)

**The current version of the RAML specification is 1.0 - and you can find it [here](https://github.com/raml-org/raml-spec/blob/master/versions/raml-10/raml-10.md).**

RAML is a language for the definition of HTTP-based APIs that embody most or all of the principles of Representational State Transfer (REST). The RAML specification (this document) defines an application of the [YAML 1.2 specification](http://yaml.org/spec/1.2/spec.html) that provides mechanisms for the definition of practically-RESTful APIs, while providing provisions with which source code generators for client and server source code and comprehensive user documentation can be created.

Why not pay us a visit on [raml.org](http://www.raml.org)? You will find tons of information around RAML such as a tutorial, what the RAML Workgroup is, RAML projects, a forum, and a lot more.

## What is the fastest way to get started?

All you need is an editor of your choice - we recommend either MuleSoft's [API Designer](https://github.com/mulesoft/api-designer) or [API Workbench](http://apiworkbench.com/); but any text editor will do just fine.

Now you only need to do is to write the design for your first endpoint

```yaml
1     #%RAML 1.0
2     title: D-Car
3     description: Domain API providing static and dynamic car data
4     version: v1
5     mediaType: application/json
6     uses:   
7       types: exchange_modules/.../f-ccsappdatatypes.raml
8     types:
9       Car:  types.Car
10       Vin:  types.Vin
11      Vins: types.Vins  
12    documentation: 
13    - title: Data Definition Table 
14      content: !include docs/dtdCar.md
15
16    /cars:
17      description: All cars
18      get:
19        description: Get VINs of all cars
20        responses:
21          200:
22            body:
23              type: Vins
24
25      /{vin}:
26        description: A specific car identified by its VIN
27        uriParameters:
28          vin:
29          type: Vin
30        put:
31          description: Update a car
32          body:
33            type: Car
34          responses:
35            404:
36              body:
37                properties:
38                  error: string
39              example:
40                error: "No Vehicle found for the given VIN" 
```

```yaml
1     #%RAML 1.0

3     title: D-Car
4     description: Domain API providing static and dynamic car data
5     version: v1
6     mediaType: application/json
7     uses:   
8       types: exchange_modules/.../f-ccsappdatatypes.raml
9     types:
10       Car:  types.Car
11      Vin:  types.Vin
12      Vins: types.Vins  
13    documentation: 
14    - title: Data Definition Table 
15      content: !include docs/dtdCar.md

17    /cars:
18      ...
19
20      /{vin}:
21         ...
```

Interested? Learn more about the syntax in the [RAML 1.0 specification](https://github.com/raml-org/raml-spec/blob/master/versions/raml-10/raml-10.md) or take a look at some [examples](https://github.com/raml-org/raml-examples).

## How do I learn more?

* [Tutorial](http://raml.org/developers/raml-100-tutorial)
* [Advanced Tutorial](http://raml.org/developers/raml-200-tutorial)
* [Examples](https://github.com/raml-org/raml-examples)
* [Blog](https://medium.com/raml-api)
* [Projects](http://www.raml.org/projects)

## How can I contribute?

We welcome any contributions from the community! You can contribute or provide feedback for the RAML Specification in different ways depending on your intentions. The following table illustrates the different ways to help us not only to improve the documentation of the specification, but also RAML itself.

|Your Intention  |What to do?|
|:----------|:----------|
|You see a spelling or grammar mistake, or an error in our examples? | Fork this repository, make edits, and then submit a pull request. We will respond to your request as quickly as possible.
|You want to suggest a new feature, improve existing features, ask questions, or things in general around the RAML specification? | File an issue. Please be as specific as possible about your intentions or what you’d like to see.

## How can I get in touch?

* [Slack](https://raml.org/slack)
* [@ramlapi](https://twitter.com/ramlapi)
* info@raml.org
* [Forum](http://forum.raml.org)
* [Stack Overflow](http://stackoverflow.com/questions/tagged/raml)
* [Github Issues](https://github.com/raml-org/raml-spec/issues)

## Licensing

[Branding Guidelines](http://raml.org/licensing.html)
