---
title: Introducing the Knot.x Extension Maven Archetype
description: "Writing a custom Knot.x Extension just became easier with the release of the Knot.x Extension Maven Archetype."
author: toniedzwiedz
date: 2017-02-23
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
