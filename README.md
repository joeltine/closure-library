# Closure Library [![Build Status](https://travis-ci.org/google/closure-library.svg?branch=master)](https://travis-ci.org/google/closure-library)

Closure Library is a powerful, low-level JavaScript library designed
for building complex and scalable web applications. It is used by many
Google web applications, such as Google Search, Gmail, Google Docs,
Google+, Google Maps, and others.

For more information, visit the
[Google Developers](https://developers.google.com/closure/library) or
[GitHub](https://github.com/google/closure-library) sites.

Download the latest stable version on our [releases page](https://github.com/google/closure-library/releases).

Developers, please see the
[Generated API Documentation](http://google.github.io/closure-library/api/).

See also the
[goog.ui Demos](http://google.github.io/closure-library/source/closure/goog/demos/)

## Conceptual Introduction

Closure Library goes against what are established norms in the JS community. For example, code compactness and API overloading (e.g., jquery) are considered "best practice" in the open-source community, even in uncompiled code. What people don't understand about Closure Library is that we're considering dead code removal via JS Compiler an inherent part of the process. This allows us to focus on creating high quality APIs that are maintainable and scale well. As a result, our code looks archaic and verbose to those not familiar with the Compiler. We could've done a much better job selling it this way though.
 
"Using Closure essentially extends JavaScript to include features available in
other programming languages, such as namespaces, type checking, and data hiding.
Furthermore, it does so without incurring the runtime overhead of previous
approaches. More importantly, it does not sacrifice the good parts of JavaScript
(prototypal inheritance, regular expression literals, first-class functions)
that are not available in other programming languages, such as Java. This
transforms JavaScript from a language one must "deal with" into one that is fun
and productive."

[Closure: The Definitive Guide]:http://www.amazon.com/Closure-Definitive-Guide-Michael-Bolin/dp/1449381871

## Design principles

### Compilation support is critical

Closure library was specifically designed to be compiled using the Closure
Compiler. Therefore, when compiling Closure you should be confident that it will
be minimized as efficiently as possible with all of the strictest compilation
options.

With Closure, it's important to keep in mind that the verbosity of the code is
a secondary consideration compared to its size after being processed by the
Compiler. It is always preferable to write more code (or annotations) that
results in smaller compiled output, than to use compact syntax that may result
in larger compiled code.

### Memory matters

JavaScript is a language that manages its own memory. As such, the possibility
of leaking memory is real and the progammer needs to ensure that references to
objects that are no longer needed are released as soon as possible. Closure
Library uses `goog.Disposable` to ensure that references are managed
intelligently to complement garbage collection.

### Errors are caught at compile time

Closure Library takes full advantage of the, comment-based, type and visibility
annotations supported by the Closure Compiler. This allows the Compiler to
verify the types passed and returned from methods are correct. Also, this
enables enforcement of standard visibility constructs common in other
programming languages (e.g., public, private, protected, etc.). Using these
annotations in conjunction with the Compiler greatly increases confident in
the code's correctness.

### Code works without compilation

Although first-class Closure Compiler compilation support is a core design
principle, the Closure Library also is expected to be run without being
processed by the Compiler. This concept is necessary to ensure Closure remains
"just JavaScript" and can be debugged easily.

### Cross-browser compatible

A fundamental aspect of the utility Closure Library provides is cross-browser
compatability. All of Closure's libraries are expected to be fully functional
across all, popular, modern and legacy browsers. This philosophy insulates
developers from the nightmare of cross-browser compatibility issues that exist
in the wild.

### Built-in types are never modified

The, native, built-in browser types should never be augmented or changed by
Closure. This is key in ensuring Closure's compatibility with other JS libraries
and frameworks.

### Tooling is independent

When using Closure, you should never be forced to use any one tool of the
library. For example, you can use the Compiler without using Closure Library and
vice versa; or, perhaps you choose to forgo Closure's testing infrastructure but
still use individual libraries piecemeal. That said, Closure tools lose some
effectiveness when used on their own. To get the most out of Closure, you should
be using its tools together where possible.

## Using with Node.js
Install the [official package](https://www.npmjs.com/package/google-closure-library) from npm.

```
npm install google-closure-library
```

Require the package and use goog.require normally.

```
require("google-closure-library");

goog.require("goog.crypt.Sha1");

var sha1 = new goog.crypt.Sha1();
sha1.update("foobar");
var hash = sha1.digest();
```
