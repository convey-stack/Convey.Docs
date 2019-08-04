# Welcome to Convey

Convey is a set of **helper libraries** that can be most of the time (with some exceptions) **used independently of each other** in order to help you to build your web applications and micro services. **Convey is neither a framework, nor a silver bullet**. 

Quite opposite, **it's mostly the set of extensions methods along with additional abstractions** that will help you to deal with common infrastructural concerns such as routing, service discovery, load balancing, tracing, asynchronous messaging and so on.

In order to find out how you can **use Convey in a real-world scenarios,** take a look at the sample projects available on our [DevMentors.io](https://devmentors.io) GitHub [organization](https://github.com/devmentors). There are 3 projects for now: 

* **[Pacco](https://github.com/devmentors/Pacco)** - the most advanced one, tackling the exclusive parcels' delivery domain, consisting of about 10 microservices
* **[NPost](https://github.com/devmentors/NPost)** - only a few services, and rather simple parcel delivery domain 
* **[DShop](https://github.com/devmentors/DNC-DShop)** - doesn't use Convey, but instead contains the so-called **Common** project which was one of the reasons why we started building Convey (by splitting up into smaller, independent pieces a single shared library).

And if you're looking for the resources about building microservices with .NET Core, **check out our free course** available on YouTube (almost 20 hours) titled [Distributed .NET Core](https://devmentors.io/distributed-net-core).

Eventually, feel free to take a look at our other projects that you might find useful when building the distributed services:

* **[Chronicle](https://github.com/chronicle-stack/chronicle)** - a simple process manager/saga pattern implementation for .NET Core that helps you manage long-living and disitrbuted transactions.
* **[Ntrada](https://github.com/Ntrada/Ntrada)** - API Gateway built with .NET Core, that can be easily configured with yaml files and doesn't require additional coding whatsoever.