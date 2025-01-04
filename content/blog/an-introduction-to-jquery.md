---
title: 'An introduction to jQuery'
date: 2011-11-16T19:15:00.001-06:00
draft: true
url: 
tags: 
- jQuery
---

**What is jQuery ?** [jQuery](http://jquery.com/) is a fast and concise JavaScript Library that simplifies HTML document traversing, event handling, animating, and Ajax interactions for rapid web development.

**Get jQUery** jQuery is licensed under MIT and GPL. You can downlad the latest version from [http://docs.jquery.com/Downloading\_jQuery](http://docs.jquery.com/Downloading_jQuery). In this post we will use release 1.7.

**Getting started**

To get started with jQuery, create a folder for our demos. Create a new file in it (e.g. HTMLPage1.htm). Create a folder in it (e.g. Script). Copy the downloaded _jquery-1.7.js_ to it. Now edit your HTML page to look like so:

<br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

```
 1: <html xmlns\="http://www.w3.org/1999/xhtml"\>
```  
  
```
 2: <head\>
```  
  
```
 3:    <title\>Demo 1</title\>
```  
  
```
 4:    <script src\="Script/jquery-1.7.js" type\="text/javascript"\>
```  
  
```
 5:    </script\>
```  
  
```
 6:    <script type="text/javascript"\>
```  
  
```
 7:        $(document).ready(function () {
```  
  
```
 8:            $("<div><b> Hello World</b><br /> This is a new div added to the page using jQuery</div>").appendTo("body");
```  
  
```
 9:        });
```  
  
```
 10:    </script\>
```  
  
```
 11: </head\>
```  
  
```
 12: <body\>
```  
  
```
 13: </body\>
```  
  
```
 14: </html\>
```  

  
  

If you open your page in any browser, it should show you the above text.

  
  

The above HTML page is a typical HTML page that have link to jQuery source. Lines 6-10 are our first introduction to JQuery.

  
  

Adding the jQuery library to your pages is like adding any JavaScript file to your page. Just download the latest version and add like to it on your page.

  
  

Basically, jQuery syntax is made for selecting HTML elements and perform some action on that element (s). Basic syntax is: **$(selector).action/event()**

  
  

  
*   A dollar sign to define jQuery
  
  
*   A (selector) to "query (or find)" HTML elements
  
  
*   A jQuery action() to be performed on the element(s)
  

  
  

In our case the selector is trying to find the page document. The event is [**ready**](http://api.jquery.com/ready/)**,** which is fired when the page [DOM](http://www.w3schools.com/htmldom/default.asp) if fully loaded. The ready event take a handler to be executed as soon as the DOM hierarchy has been fully constructed, so it is the best place to attach all other event handlers and run other jQuery code. In our case we just try to append a div to the HTML body.

  
  

jQuery Selectors

  
  

jQuery selectors allow you to select and manipulate HTML elements as a group or as a single element by element name, attribute name or by content. jQuery uses CSS selectors to select HTML elements: $(“p”) selects all <p> elements. jQuery also uses XPath expressions to select elements with given attributes: $(“\[href\]”) select all elements with an href attribute. To make it easy to remember, selectors may fall into the following categories:

  
  

**Basic Selectors** based on CSS 1 specification

  
  

  
*   **(“\*”)**     selects all elements
  
  
*   **(“element”)**     selects all elements with the given tag name. This selector calls JavaScript’s function getElementsByTagName() to return the appropriate elements.  
  
  
*   **(“.class”)**     selects all elements with the given class
  
  
*   **(“#id”)**     selects a single element with the given id attribute
  
  
*   **(“selector1, selector2, selectorN”)**      selects the combined results of all the specified selectors.
  

  
  

**Attribute Selectors** used to identify elements by their attributes.

  
  

  
*   **\[name\]** selects elements that have the specified attribute with any value. $(‘div\[id\]’) selects all DIV elements that have id attribute, regardless to the id value.
  
  
*   **\[name=”value”\]** selects elements that have the specified attribute with a value exactly equal to a certain value. $(‘input\[value=”test value”\]’ selects all inputs with a value of “test value”
  
  
*   **\[name|=”value”\]**     selects elements that have the specified attribute with value either equal to a given string or starting with that string followed by a hyphen(-). `$('a[hreflang|="en"]') f`inds all links with an hreflang attribute that is english.
  
  
*   **\[name\*=”value”\]**     Selects elements that have the specified attribute with a value containing the a given substring. $(‘input\[name\*=””\]’) finds all inputs with a name attribute that contains 'man'
  
  
*   **\[name~=”value”\]**     Selects elements that have the specified attribute with a value containing a given word, delimited by spaces. $(‘input\[name~=”man”\]’) finds all inputs with a name attribute that contains the word 'man'
  
  
*   **\[name$=”value”\]**     Selects elements that have the specified attribute with a value ending exactly with a given string. The comparison is case sensitive. $(‘input\[name$=”letter”\]’) finds all inputs with an attribute name that ends with 'letter'
  
  
*   **\[name!=”value”\]**     Select elements that either don't have the specified attribute, or do have the specified attribute but not with a certain value. $(‘input\[name!=”newsletter”\]’)finds all inputs that don't have the name 'newsletter'
  
  
*   **\[name^=”news”\]**     Selects elements that have the specified attribute with a value beginning exactly with a given string. $(‘input\[name^=”news”\]’) finds all inputs with an attribute name that starts with 'news'
  
  
*   **\[name=”value”\]\[name2=”value2”\]**     Selects elements that match all of the specified attribute filters. $(‘input\[id\]\[name$=”man”\]’) finds all inputs that have an id attribute and whose name attribute ends with man
  

  
  

**Form Selectors** used to select form elements

  
  

  
*   **(‘:button’)**     Selects all button elements and elements of type button. To achieve the best performance first select the elements using an attribute selector, then use[`.filter(":button")`](http://api.jquery.com/filter/).
  
  
*   **(‘:checkbox’)**     Selects all elements of type checkbox. For better performance in modern browsers, use`[type="checkbox"]`
  
  
*   `**(‘:checked’)**     Selects all checkboxes and radio buttons that are checked.`
  
  
*   `**(‘:disabled’)**     Selects all elements that are disabled.`
  
  
*   **(‘:enabled’)**     Selects all elements that are enabled.
  
  
*   **(‘:file’)**     Selects all elements of type file. For better performance in modern browsers, use`[type="file"]` .
  
  
*   **(‘:focus’)**     Selects element if it is currently focused. If you are looking for the currently focused element, `$( document.activeElement )` will retrieve it for you.
  
  
*   **(‘:image’)**     Selects all elements of type image. For better performance in modern browsers, use`[type="image"]`.
  
  
*   **(‘:input’)**     Selects all input, textarea, select and button elements. Basically it selects all form controls. To achieve the best performance when using `:input` to select elements, first select the elements using an attribute selector, then use[`.filter(":input")`](http://api.jquery.com/filter/).
  
  
*   **(‘:password’)**     Selects all elements of type password. For better performance in modern browsers, use`[type="password"]` instead.
  
  
*   **(‘:radio’)**      Selects all elements of type radio. For better performance in modern browsers, use`[type="radio"]` instead.
  
  
*   **(‘:reset’)**     Selects all elements of type reset. For better performance in modern browsers, use`[type="reset"]` instead.
  
  
*   **(‘:selected’)**      Selects all elements that are selected. To achieve the best performance first select the elements using an attribute selector, then use [`.filter(":selected")`](http://api.jquery.com/filter/).
  
  
*   **(‘:submit’)**     Selects all elements of type submit. For better performance in modern browsers, use`[type="submit"]` instead.
  
  
*   **(‘:text’)**     Selects all elements of type text. For better performance in modern browsers, use`[type="text"]` instead.
  

  
  

**Hierarchy Selectors** used to traverse the DOM tree.

  
  

  
*   **(‘parent > child’)**     Selects all direct child elements specified by "child" of elements specified by "parent". $(“ul.className > li”) selects all list items that are children of <ul class=”className”>.
  
  
*   **(‘ancestor descendant’)**     Selects all elements that are descendants of a given ancestor. A descendant of an element could be a child, grandchild, great-grandchild, and so on, of that element. $(“form input”) selects all input descendants of form.  
      
    
      
    *   ancestor : Any valid selector.
      
      
    *   descendant : A selector to filter the descendant elements.
      
    
      
    
  
  
*   **(‘prev + next’)**     Selects all next elements matching "next" that are immediately preceded by a sibling "prev". Both must share the same parent. $(“label + input”) selects all inputs that are next to a label.  
      
    
      
    *   prev: Any valid selector
      
      
    *   next: A selector to match the element that is next to the first selector.
      
    
      
    
  
  
*   **(‘prev ~ siblings’)**     Selects all sibling elements that follow after the "prev" element, have the same parent, and match the filtering "siblings" selector (doesn’t select siblings’ children).  
      
    
      
    *   prev : Any valid selector
      
      
    *   siblings :  A selector to filter elements that are the following siblings of the first selector.