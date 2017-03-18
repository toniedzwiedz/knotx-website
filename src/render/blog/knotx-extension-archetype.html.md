---
title: Introducing the Knot.x Extension Maven Archetype
description: "Writing a custom Knot.x Extension just became easier with the release of the Knot.x Extension Maven Archetype."
author: toniedzwiedz
date: 2017-03-20
---
## Knot.x Extension Maven Archetype

If you followed [the last tutorial published on the Knot.x Blog](http://knotx.io/blog/adapt-service-without-webapi/), you should have a general idea
of what needs to be done to build your own _Knot.x_ extension. You may also
have noticed that it took us a bit of time to create all the necessary files. 
After all, it isn't often that you build a `pom.xml` file from scratch, is it?

Thankfully, our days of doing so are over! The [_Knot.x Extension Maven Archetype_](https://github.com/Knotx/knotx-extension-archetype)
is here and it takes care of the uninteresting boilerplate every project needs.

It comes with a couple HTML templates served from a local repository, several Java classes exemplifying the most common
extension points of _Knot.x_:

- _Service Adapter_
- _Action Adapter_
- custom _Knot_
- _Handlebars Helper_

and a set of configuration files. In other words, a solid scaffolding and simple
examples to get you started with your work. Be it a quick prototype or proper integration with
external Services using server-side templating.

Just use the following command and enjoy your new project:

    mvn archetype:generate -DarchetypeGroupId=io.knotx.archetypes -DarchetypeArtifactId=knotx-extension-archetype -DarchetypeVersion=1-SNAPSHOT

That's it! You can start developing your own extensions. Go on and try it out... or stick with us a little longer if you want to learn more about
the most common use cases for _Knot.x_ extensions.

## Choosing Your Extension Type 

As we've already mentioned, there are four basic ways _Knot.x_ can be extended with custom code. Let's have a look at when each of those
could come in handy and how it all fits into the bigger picture of a web project.

You'll be pleased to know that the archetype provides you with the necessary setup to start working on any or all of these extensions.

### Service Adapter

A _Service Adapter_ is used when we need to read data from an external source. [As we've seen before](http://knotx.io/blog/hello-rest-service/),
just calling a service over HTTP does not always require us to write any custom code. Simple prototyping based on read-only endpoints can be
done using the out-of-the-box (OOTB) `ServiceAdapter` and a sprinkle of configuration.

However, if the data source uses a different protocol or if there is some non-trivial
logic behind building an HTTP request, extending the _Service Adapter_ is the way to go.

You can see an example of a custom _Service Adapter_ connecting directly to a relational database in
[the previous tutorial](http://knotx.io/blog/adapt-service-without-webapi/).

### Action Adapter

A _Service Adapter_, as understood in the _Knot.x_ nomenclature, is capable of reading data from external sources. 
The _Action Adapter_ is its counterpart responsible for handling requests that are supposed to modify some
externally available data.

This is where the complexity behind most Web APIs really sits, making _Action Adapters_ the most commonly implemented
type of _Knot.x_ extensions across various projects.

An _Action Adapter_ can be used to handle form submission, send a request to one or more external systems, receive the result,
merge it with HTML templates obtained from a repository, and present it to the user.

### Custom Knot

A _Knot_ is an arbitrary unit of functionality. If you're familiar with _Vert.x_, you can think of it as a special kind of _Verticle_
that you can configure and which can be used at some point in the templating pipeline.
 
Have a look at the HTML templates provided with the archetype and see how they declare a list of _Knots_ that they require
using the `data-knotx-knots` attribute.

For the most basic use cases, you could do without implementing any _Knots_ of your own.
However, they're a convenient way of plugging in completely arbitrary logic. For example, you could use one to do something to an
entire _Template Fragment_.


As a matter of fact, if you look at the way _Knot.x_ is implemented, you will find that  both kinds of _Adapters_ 
are just extensions to special _Knots_ available OOTB. 

### Handlebars Helper

_Knot.x_ uses [_Handlebars Java_](https://github.com/jknack/handlebars.java) as its default Template Engine. On top of being
a reasonably powerful language of its own, _Handlebars_ can be [extended with custom helpers](https://github.com/jknack/handlebars.java#helpers).
These can help you avoid repetitive and verbose code belonging to the presentation layer.

Writing custom _Handlebars_ helpers is useful when you have to render a lot of markup or display something that is otherwise  difficult
for a programmer to type in a template file.

## Enjoy!

That's all folks! Thanks for reading. We hope you'll find the new archetype useful.
 
Please let us know what you think of it. If you have any questions, feel free to
[log an issue on GitHub](https://github.com/Knotx/knotx-extension-archetype/issues) or drop us a line in the
[Knot.x Gitter chat](https://gitter.im/Knotx/Lobby).

See you around!

