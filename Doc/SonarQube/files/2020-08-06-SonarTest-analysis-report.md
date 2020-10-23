# Code analysis
## SonarTest 
#### Version 0.0.1 

**By: default**

*Date: 2020-08-06*

## Introduction
This document contains results of the code analysis of SonarTest



## Configuration

- Quality Profiles
    - Names: Sonar way [CSS]; Sonar way [JavaScript]; 
    - Files: AXO9OmHBMhI8b8VPHXKI.json; AXO9OmPAMhI8b8VPHXSK.json; 
 - Quality Gate
    - Name: Sonar way
    - File: Sonar way.xml

## Synthesis
Quality Gate | Reliability | Security | Maintainability | Coverage | Duplications
:---:|:---:|:---:|:---:|:---:|:---:
OK | E | A | A | 0.0 % | 1.4 %

## Metrics

\ | Cyclomatic Complexity | Cognitive Complexity | Lines of code per file | Coverage | Comment density (%) | Duplication (%)
:---|:---:|:---:|:---:|:---:|:---:|:---:
Min | 0.0 | 0.0 | 5.0 | 0.0 | 0.0 | 0.0
Max | 679.0 | 362.0 | 3713.0 | 0.0 | 45.9 | 86.7

## Volume

Language|Number
---|---
CSS|158
JavaScript|3555
Total|3713


## Issues count by severity and types

Type|Severity|Number
---|---|---
VULNERABILITY|BLOCKER|0
VULNERABILITY|CRITICAL|0
VULNERABILITY|MAJOR|0
VULNERABILITY|MINOR|0
VULNERABILITY|INFO|0
BUG|BLOCKER|1
BUG|CRITICAL|0
BUG|MAJOR|35
BUG|MINOR|13
BUG|INFO|0
CODE_SMELL|BLOCKER|0
CODE_SMELL|CRITICAL|0
CODE_SMELL|MAJOR|12
CODE_SMELL|MINOR|4
CODE_SMELL|INFO|0
SECURITY_HOTSPOT|BLOCKER|0
SECURITY_HOTSPOT|CRITICAL|0
SECURITY_HOTSPOT|MAJOR|0
SECURITY_HOTSPOT|MINOR|0
SECURITY_HOTSPOT|INFO|0


## Issues
Name|Description|Type|Severity|Number
---|---|---|---|---
Callbacks of array methods should have return statements|Arrays in JavaScript have several methods for filtering, mapping or folding that require a callback. Not having a return statement in such a <br /> callback function is most likely a mistake. <br /> This rule applies for the following methods of an array: <br />  <br />    Array.from  <br />    Array.prototype.every  <br />    Array.prototype.filter  <br />    Array.prototype.find  <br />    Array.prototype.findIndex  <br />    Array.prototype.map  <br />    Array.prototype.reduce  <br />    Array.prototype.reduceRight  <br />    Array.prototype.some  <br />    Array.prototype.sort  <br />  <br /> Noncompliant Code Example <br />  <br /> var merged = arr.reduce(function(a, b) { <br />   a.concat(b); <br /> }); // Noncompliant: No return statement <br />  <br /> Compliant Solution <br />  <br /> var merged = arr.reduce(function(a, b) { <br />   return a.concat(b); <br /> }); <br /> |BUG|BLOCKER|1
Font declarations should contain at least one generic font family|If none of the font names defined in a font or font-family declaration are available on the browser of the user, the <br /> browser will display the text using its default font. It's recommended to always define a generic font family for each declaration of <br /> font or font-family to get a less degraded situation than relying on the default browser font. All browsers should implement <br /> a list of generic font matching these families: Serif, Sans-serif, cursive, fantasy, <br /> Monospace. <br /> Noncompliant Code Example <br />  <br /> a { <br />   font-family: Helvetica, Arial, Verdana, Tahoma; /* Noncompliant; there is no generic font family in the list */ <br /> } <br />  <br /> Compliant Solution <br />  <br /> a { <br />   font-family: Helvetica, Arial, Verdana, Tahoma, sans-serif; <br /> } <br />  <br /> See <br />  <br />    CSS Specification - Generic font families  <br /> |BUG|MAJOR|28
Properties should not be duplicated|CSS allows duplicate property names but only the last instance of a duplicated name determines the actual value that will be used for it. <br /> Therefore, changing values of other occurrences of a duplicated name will have no effect and may cause misunderstandings and bugs. <br /> This rule ignores $sass, @less, and var(--custom-property) variable syntaxes. <br /> Noncompliant Code Example <br />  <br /> a { <br />   color: pink; <br />   background: orange; <br />   color: orange <br /> } <br />  <br /> Compliant Solution <br />  <br /> a { <br />   color: pink; <br />   background: orange <br /> } <br /> |BUG|MAJOR|6
Strict equality operators should not be used with dissimilar types|Comparing dissimilar types using the strict equality operators === and !== will always return the same value, <br /> respectively false and true, because no type conversion is done before the comparison. Thus, such comparisons can only be <br /> bugs. <br /> Noncompliant Code Example <br />  <br /> var a = 8; <br /> var b = "8"; <br />  <br /> if (a === b) {  // Noncompliant; always false <br />   // ... <br /> } <br />  <br /> Compliant Solution <br />  <br /> var a = 8; <br /> var b = "8"; <br />  <br /> if (a == b) { <br />   // ... <br /> } <br />  <br /> or <br />  <br /> var a = 8; <br /> var b = "8"; <br />  <br /> if (a === Number(b)) { <br />   // ... <br /> } <br /> |BUG|MAJOR|1
"<strong>" and "<em>" tags should be used|The &lt;strong&gt;/&lt;b&gt; and &lt;em&gt;/&lt;i&gt; tags have exactly the same effect in most <br /> web browsers, but there is a fundamental difference between them: &lt;strong&gt; and &lt;em&gt; have a semantic meaning <br /> whereas &lt;b&gt; and &lt;i&gt; only convey styling information like CSS.  <br /> While &lt;b&gt; can have simply no effect on a some devices with limited display or when a screen reader software is used by a blind <br /> person, &lt;strong&gt; will: <br />  <br />    Display the text bold in normal browsers  <br />    Speak with lower tone when using a screen reader such as Jaws  <br />  <br /> Consequently: <br />  <br />    in order to convey semantics, the &lt;b&gt; and &lt;i&gt; tags shall never be used,  <br />    in order to convey styling information, the &lt;b&gt; and &lt;i&gt; should be avoided and CSS should be used instead. <br />    <br />  <br /> Noncompliant Code Example <br />  <br /> &lt;i&gt;car&lt;/i&gt;             &lt;!-- Noncompliant --&gt; <br /> &lt;b&gt;train&lt;/b&gt;         &lt;!-- Noncompliant --&gt; <br />  <br /> Compliant Solution <br />  <br /> &lt;em&gt;car&lt;/em&gt; <br /> &lt;strong&gt;train&lt;/strong&gt; <br />  <br /> Exceptions <br /> This rule is relaxed in case of icon <br /> fonts usage. <br />  <br /> &lt;i class="..." aria-hidden="true" /&gt;    &lt;!-- Compliant icon fonts usage --&gt; <br /> |BUG|MINOR|6
Image, area and button with image tags should have an "alt" attribute|The alt attribute provides a textual alternative to an image. <br /> It is used whenever the actual image cannot be rendered. <br /> Common reasons for that include: <br />  <br />    The image can no longer be found  <br />    Visually impaired users using a screen reader software  <br />    Images loading is disabled, to reduce data consumption on mobile phones  <br />  <br /> It is also very important to not set an alt attribute to a non-informative value. For example &lt;img ... alt="logo"&gt; <br /> is useless as it doesn't give any information to the user. In this case, as for any other decorative image, it is better to use a CSS background image <br /> instead of an &lt;img&gt; tag. If using CSS background-image is not possible, an empty alt="" is tolerated. See Exceptions <br /> bellow. <br /> This rule raises an issue when <br />  <br />    an &lt;input type="image"&gt; tag or an &lt;area&gt; tag have no alt attribute or their <br />   alt&nbsp;attribute has an empty string value.  <br />    an &lt;img&gt; tag has no alt attribute.  <br />  <br /> Noncompliant Code Example <br />  <br /> &lt;img src="foo.png" /&gt; &lt;!-- Noncompliant --&gt; <br /> &lt;input type="image" src="bar.png" /&gt; &lt;!-- Noncompliant --&gt; <br /> &lt;input type="image" src="bar.png" alt="" /&gt; &lt;!-- Noncompliant --&gt; <br />  <br /> &lt;img src="house.gif" usemap="#map1" <br />     alt="rooms of the house." /&gt; <br /> &lt;map id="map1" name="map1"&gt; <br />   &lt;area shape="rect" coords="0,0,42,42" <br />     href="bedroom.html"/&gt; &lt;!-- Noncompliant --&gt; <br />   &lt;area shape="rect" coords="0,0,21,21" <br />     href="lounge.html" alt=""/&gt; &lt;!-- Noncompliant --&gt; <br /> &lt;/map&gt; <br />  <br /> Compliant Solution <br />  <br /> &lt;img src="foo.png" alt="Some textual description of foo.png" /&gt; <br /> &lt;input type="image" src="bar.png" alt="Textual description of bar.png" /&gt; <br />  <br /> &lt;img src="house.gif" usemap="#map1" <br />     alt="rooms of the house." /&gt; <br /> &lt;map id="map1" name="map1"&gt; <br />   &lt;area shape="rect" coords="0,0,42,42" <br />     href="bedroom.html" alt="Bedroom" /&gt; <br />   &lt;area shape="rect" coords="0,0,21,21" <br />     href="lounge.html" alt="Lounge"/&gt; <br /> &lt;/map&gt; <br />  <br /> Exceptions <br /> &lt;img&gt; tags with empty string&nbsp;alt="" attributes won't raise any issue. However this technic should be used in <br /> two cases only: <br /> When the image is decorative and it is not possible to use a CSS background image. For example, when the decorative &lt;img&gt; is <br /> generated via javascript with a source image coming from a database, it is better to use an &lt;img alt=""&gt; tag rather than generate <br /> CSS code. <br />  <br /> &lt;li *ngFor="let image of images"&gt; <br />     &lt;img [src]="image" alt=""&gt; <br /> &lt;/li&gt; <br />  <br /> When the image is not decorative but it's alt text would repeat a nearby text. For example, images contained in links should not <br /> duplicate the link's text in their alt attribute, as it would make the screen reader repeat the text twice. <br />  <br /> &lt;a href="flowers.html"&gt; <br />     &lt;img src="tulip.gif" alt="" /&gt; <br />     A blooming tulip <br /> &lt;/a&gt; <br />  <br /> In all other cases you should use CSS background images. <br /> See&nbsp;W3C WAI&nbsp;Web Accessibility Tutorials&nbsp;for more <br /> information. <br /> See <br />  <br />    WCAG2, H24 - Providing text alternatives for the area elements of image maps  <br />    WCAG2, H36 - Using alt attributes on images used as submit buttons  <br />    WCAG2, H37 - Using alt attributes on img elements  <br />    WCAG2, H67 - Using null alt text and no title attribute on img elements for images <br />   that AT should ignore  <br />    WCAG2, H2 - Combining adjacent image and text links for the same resource  <br />    WCAG2, 1.1.1 - Non-text Content  <br />    WCAG2, 2.4.4 - Link Purpose (In Context)  <br />    WCAG2, 2.4.9 - Link Purpose (Link Only)  <br /> |BUG|MINOR|7
Sections of code should not be commented out|Programmers should not comment out code as it bloats programs and reduces readability. <br /> Unused code should be deleted and can be retrieved from source control history if required.|CODE_SMELL|MAJOR|1
Empty blocks should be removed|Leftover empty blocks are usually introduced by mistake. They are useless and prevent readability of the code. They should be removed or completed <br /> with real code. <br /> Noncompliant Code Example <br />  <br /> a { } <br />  <br /> Compliant Solution <br />  <br /> a { color: pink; } <br /> |CODE_SMELL|MAJOR|3
Selectors should not be duplicated|Duplication of selectors might indicate a copy-paste mistake. The rule detects the following kinds of duplications: <br />  <br />    within a list of selectors in a single rule set  <br />    for duplicated selectors in different rule sets within a single stylesheet.  <br />  <br /> Noncompliant Code Example <br />  <br /> .foo, .bar, .foo { ... }  /* Noncompliant */ <br />  <br /> .class1 { ... } <br /> .class1 { ... }  /* Noncompliant */ <br />  <br /> Compliant Solution <br />  <br /> .foo, .bar { ... } <br />  <br /> .class1 { ... } <br /> .class2 { ... } <br /> |CODE_SMELL|MAJOR|4
CSS files should not be empty|This rule raises an issue when a CSS file is empty (ie: containing only spaces).|CODE_SMELL|MAJOR|2
Variables should not be shadowed|Overriding or shadowing a variable declared in an outer scope can strongly impact the readability, and therefore the maintainability, of a piece of <br /> code. Further, it could lead maintainers to introduce bugs because they think they're using one variable but are really using another. <br /> See <br />  <br />    CERT, DCL01-C. - Do not reuse <br />   variable names in subscopes  <br />    CERT, DCL51-J. - Do <br />   not shadow or obscure identifiers in subscopes  <br /> |CODE_SMELL|MAJOR|1
Array-mutating methods should not be used misleadingly|Many of JavaScript's Array methods return an altered version of the array while leaving the source array intact. reverse <br /> and sort do not fall into this category. Instead, they alter the source array in addition to returning the altered version, <br /> which is likely not what was intended. <br /> This rule raises an issue when the return values of these methods are assigned, which could lead maintainers to overlook the fact that the original <br /> value is altered. <br /> Noncompliant Code Example <br />  <br /> var b = a.reverse(); // Noncompliant <br /> var d = c.sort(); // Noncompliant <br />  <br /> Compliant Solution <br />  <br /> var b = [...a].reverse();  // de-structure and create a new array, so reverse doesn't impact 'a' <br /> a.reverse(); <br />  <br /> c.sort(); // this sorts array in place <br /> |CODE_SMELL|MAJOR|1
Return of boolean expressions should not be wrapped into an "if-then-else" statement|Return of boolean literal statements wrapped into if-then-else ones should be simplified.  <br /> Note that if the result of the expression is not a boolean but for instance an integer, then double negation should be used for proper <br /> conversion. <br /> Noncompliant Code Example <br />  <br /> if (expression) { <br />   return true; <br /> } else { <br />   return false; <br /> } <br />  <br /> Compliant Solution <br />  <br /> return expression; <br />  <br /> or  <br />  <br /> return !!expression; <br /> |CODE_SMELL|MINOR|1
"switch" statements should have at least 3 "case" clauses|switch statements are useful when there are many different cases depending on the value of the same expression. <br /> For just one or two cases however, the code will be more readable with if statements. <br /> Noncompliant Code Example <br />  <br /> switch (variable) { <br />   case 0: <br />     doSomething(); <br />     break; <br />   default: <br />     doSomethingElse(); <br />     break; <br /> } <br />  <br /> Compliant Solution <br />  <br /> if (variable == 0) { <br />   doSomething(); <br /> } else { <br />   doSomethingElse(); <br /> } <br /> |CODE_SMELL|MINOR|1
Default export names and file names should match|By convention, a file that exports only one class, function, or constant should be named for that class, function or constant. Anything else may <br /> confuse maintainers. <br /> Noncompliant Code Example <br />  <br /> // file path: myclass.js  -- Noncompliant <br /> class MyClass { <br />   // ... <br /> } <br /> export default MyClass; <br />  <br /> Compliant Solution <br />  <br /> // file path: MyClass.js <br /> class MyClass { <br />   // ... <br /> } <br /> export default MyClass; <br />  <br /> Exceptions <br /> Case, underscores ( _ ) and dashes (-) are ignored from the name comparison.|CODE_SMELL|MINOR|2
