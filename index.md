---

layout: col-sidebar
title: OWASP Java HTML Sanitizer
tags: sanitizer
level: 3
type: tool

---

## What is this?
The OWASP HTML Sanitizer Projects provides Java based HTML sanitization of untrusted HTML!

## About 
The OWASP HTML Sanitizer is a fast and easy to configure HTML Sanitizer written in Java which lets you include HTML authored by third-parties in your web application while protecting against XSS. The existing dependencies are on guava and JSR 305. The other jars are only needed by the test suite. The JSR 305 dependency is a compile-only dependency, only needed for annotations. This code was written with security best practices in mind, has an extensive test suite, and has undergone adversarial security review. A great place to get started using the OWASP Java HTML Sanitizer is here: <a href="https://github.com/OWASP/java-html-sanitizer/blob/master/docs/getting_started.md">https://github.com/OWASP/java-html-sanitizer/blob/master/docs/getting_started.md</a>.

## Benefits
* Very easy to use. It allows for simple programmatic POSITIVE policy configuration (see below). No XML config.
* Actively maintained by Mike Samuel from Google's AppSec team!
* Passing 95+% of AntiSamy's unit tests plus many more.
* This is code from the Caja project that was donated by Google. It is rather high performance and low memory utilization.
* Java 1.5+
* Provides 4X the speed of <a href="https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project">AntiSamy</a> sanitization in DOM mode and 2X the speed of AntiSamy in SAX mode.


## Questions
*  <b>How was this project tested?</b>  This code was written with security best practices in mind, has an extensive test suite, and has undergone [adversarial security review](https://github.com/OWASP/java-html-sanitizer/blob/master/docs/attack_review_ground_rules.md).
* <b>How is this project deployed?</b> This project is best deployed through [Maven](https://github.com/OWASP/java-html-sanitizer/blob/master/docs/getting_started.md)


## Licensing
The OWASP HTML Sanitizer is free to use and is dual licensed under the <a href="http://www.apache.org/licenses/LICENSE-2.0">Apache 2 License</a> and the <a href="http://opensource.org/licenses/BSD-3-Clause">New BSD License</a>..

