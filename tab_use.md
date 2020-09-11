---
title: Use
displaytext: Use
layout: null
tab: true
order: 2
tags: sanitizer
---


## How to Use

### Maven 
The project  is available at [OWASP HTML Sanitizer : Maven Central](https://search.maven.org/#search%7Cga%7C1%7Cowasp%20html%20sanitizer)


## Creating a HTML Policy
You can view a few basic prepackaged policies for links, tables, integers, images and more here:
<https://github.com/OWASP/java-html-sanitizer/blob/master/src/main/java/org/owasp/html/Sanitizers.java>.

    `PolicyFactory policy = Sanitizers.FORMATTING.and(Sanitizers.LINKS);`
    `String safeHTML = policy.sanitize(untrustedHTML);`

The tests illustrate how to configure your own policy here:
<https://github.com/OWASP/java-html-sanitizer/blob/master/src/test/java/org/owasp/html/HtmlPolicyBuilderTest.java>


    `PolicyFactory policy = new HtmlPolicyBuilder()`
    `   .allowElements("a")`
    `   .allowUrlProtocols("https")`
    `   .allowAttributes("href").onElements("a")`
    `   .requireRelNofollowOnLinks()`
    `   .build();`
    `String safeHTML = policy.sanitize(untrustedHTML);`

... or you can write custom policies : 

    `PolicyFactory policy = new HtmlPolicyBuilder()`
    `   .allowElements("p")`
    `   .allowElements(`
    `       new ElementPolicy() {`
    `         public String apply(String elementName, List`<String>` attrs) {`
    `           attrs.add("class");`
    `           attrs.add("header-" + elementName);`
    `           return "div";`
        `         }`
    `       }, "h1", "h2", "h3", "h4", "h5", "h6"))`
    `   .build();`
    `String safeHTML = policy.sanitize(untrustedHTML);`

Please note that the elements "a", "font", "img", "input" and "span" need to be explicitly whitelisted using the \`allowWithoutAttributes()\` method if you want them to be allowed through the filter when these elements do not include any attributes.

You can also use the default "ebay" and "slashdot" policies. 
The [Slashdot policy](https://github.com/OWASP/java-html-sanitizer/blob/master/src/main/java/org/owasp/html/examples/SlashdotPolicyExample.java) allows the following tags ("a", "p", "div", "i", "b", "em", "blockquote", "tt", "strong"n "br", "ul", "ol", "li") and only certain attributes. 
This policy also allows for the custom slashdot tags,"quote" and "ecode".

### CSS Sanitization

CSS sanitization is challenging.

We disallow position:sticky and position:fixed so that client code can use a position:relative;overflow:hidden to contain self-styling sanitized snippets. Embedders of sanitized content do have to consistently do that and make sure that contributed content is clearly demarcated.

Most CSS attacks require a payload to specify selectors which the sanitizer should not allow. Unproxied images do allow tracking and, by positioning below the fold, can track whether a user scrolls down.
Embedders do need to use URL rewriting if they allow background styling and use sensible Referrer-Policy and related headers.

That said, even if care is taken, CSS has a large attack surface, so not using it puts you in a safer place.

### Inline/Embedded Images

Inline images use the data URI scheme to embed images directly within web pages. The following describes how to allow inline images in an HTML Sanitizer policy.

1\) Add the "data" protocol do your whitelist. Se example [how to add "data" protocol.](https://static.javadoc.io/com.googlecode.owasp-java-html-sanitizer/owasp-java-html-sanitizer/20160628.1/org/owasp/html/HtmlPolicyBuilder.html#allowUrlProtocols)
    `.allowUrlProtocols("data")`

2\) You can then allow an attribute with an extra check thus
    `.allowAttributes("src")`
    `.matching(...)`
    `.onElements("img")`

3\) There are a number of things you can do in the matching part such as allow the following instead of just allowing data.

### <data:image/>`...`

4\) Since allowUrlProtocols("data") allows data URLs anywhere data URLs are allowed, you might want to also add a matcher to any other URL attributes that reject anything with a colon that does not start with http: or https: or mailto:
    `.allowAttributes("href")`
    `.matching(...)`
    `.onElements("a")`
