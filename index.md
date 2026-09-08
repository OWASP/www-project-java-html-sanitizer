---

layout: col-sidebar
title: OWASP Java HTML Sanitizer
tags: sanitizer
level: 3
type: tool

---

## What is this?
The OWASP Java HTML Sanitizer Project provides Java based HTML sanitization of untrusted HTML!

## About 
The OWASP Java HTML Sanitizer is a fast and easy to configure HTML Sanitizer written in Java which lets you include HTML authored by third-parties in your web application while protecting against XSS. The sanitizer JAR has no runtime dependencies; its only compile-time dependency is <code>spotbugs-annotations</code>, which supplies annotations only. The other jars are only needed by the test suite. This code was written with security best practices in mind, has an extensive test suite, and has undergone adversarial security review. A great place to get started using the OWASP Java HTML Sanitizer is here: <a href="https://github.com/OWASP/java-html-sanitizer/blob/main/docs/getting_started.md">https://github.com/OWASP/java-html-sanitizer/blob/main/docs/getting_started.md</a>.

## Benefits
* Very easy to use. It allows for simple programmatic POSITIVE policy configuration (see below). No XML config.
* No runtime dependencies.
* Passing 95+% of AntiSamy's unit tests plus many more.
* This is code from the Caja project that was donated by Google. It is rather high performance and low memory utilization.
* Java 8+
* Provides 4X the speed of <a href="https://owasp.org/www-project-antisamy/">AntiSamy</a> sanitization in DOM mode and 2X the speed of AntiSamy in SAX mode.

## Leadership
The project was founded by <a href="https://github.com/mikesamuel">Mike Samuel</a>, then of Google's AppSec team, who wrote the original sanitizer and led it for over a decade. He has since stepped back from day-to-day maintenance.

The project is now led by <a href="https://github.com/jmanico">Jim Manico</a>, with release management and maintenance shared by <a href="https://github.com/mrabhishek">Abhishek</a>, <a href="https://github.com/aalmiray">Andres Almiray</a>, <a href="https://github.com/kittylyst">Ben Evans</a>, <a href="https://github.com/erikcostlow">Erik Costlow</a> and <a href="https://github.com/brianf">Brian Fox</a>.

## Questions
*  <b>How was this project tested?</b>  This code was written with security best practices in mind, has an extensive test suite, and has undergone [adversarial security review](https://github.com/OWASP/java-html-sanitizer/blob/main/docs/attack_review_ground_rules.md).
* <b>How is this project deployed?</b> This project is best deployed through [Maven](https://github.com/OWASP/java-html-sanitizer/blob/main/docs/getting_started.md)


## Licensing
The OWASP Java HTML Sanitizer is free to use and is dual licensed: you may use it under either the <a href="https://www.apache.org/licenses/LICENSE-2.0">Apache License, Version 2.0</a> or the <a href="https://opensource.org/licenses/BSD-2-Clause">BSD 2-Clause License</a>, at your option. See <a href="https://github.com/OWASP/java-html-sanitizer/blob/main/COPYING">COPYING</a> for the authoritative statement of the grant.
