----
Get
document.getElementById(id)	                                Find an element by element id
document.getElementsByTagName(name)	                        Find elements by tag name
document.getElementsByClassName(name)	                    Find elements by class name
const element = document.querySelector(".myClass");         Selects the first element with the class "myClass"
const x = document.querySelectorAll("p.intro");             returns a list of all <p> elements with class="intro"
document.forms["frm1"];                                     finds the form element with id="frm1", in the forms collection, and displays all element values:
    const x = document.forms["frm1"];
    let text = "";
    for (let i = 0; i < x.length; i++) {
    text += x.elements[i].value + "<br>";
    }
    document.getElementById("demo").innerHTML = text;

The following HTML objects (and object collections) are also accessible:

    document.anchors
    document.body
    document.documentElement
    document.embeds
    document.forms
    document.head
    document.images
    document.links
    document.scripts
    document.title

myTitle = document.getElementById("demo").firstChild.nodeValue;
myTitle = document.getElementById("demo").childNodes[0].nodeValue;


----
Update
properties:
element.innerHTML =  new html content	                    Change the inner HTML of an element
element.attribute = new value	                            Change the attribute value of an HTML element
element.style.property = new style	                        Change the style of an HTML element
methods:
element.setAttribute(attribute, value)	                    Change the attribute value of an HTML element
document.replaceChild(new, old)	                            Replace an HTML element

----
Create
document.createElement(element)	                            Create an HTML element
document.appendChild(element)	                            Add an HTML element
document.write(text)	                                    Write into the HTML output stream
document.getElementById(id).onclick = function(){code}	    Adding event handler code to an onclick event
document.createTextNode("This is new.");
insertBefore(para, child);

-- example with: appendchild, createElement, createTextNode 
<div id="div1">
  <p id="p1">This is a paragraph.</p>
  <p id="p2">This is another paragraph.</p>
</div>

<script>
const para = document.createElement("p");
const node = document.createTextNode("This is new.");
para.appendChild(node);

const element = document.getElementById("div1");
element.appendChild(para);
</script>


-- example with: insertBefore
<div id="div1">
  <p id="p1">This is a paragraph.</p>
  <p id="p2">This is another paragraph.</p>
</div>

<script>
const para = document.createElement("p");
const node = document.createTextNode("This is new.");
para.appendChild(node);

const element = document.getElementById("div1");
const child = document.getElementById("p1");
element.insertBefore(para, child);
</script>



----
delete
document.removeChild(element)	                            Remove an HTML element
element.removeEventListener("mousemove", myFunction);
replaceChild

-- example with: remove
<div>
  <p id="p1">This is a paragraph.</p>
  <p id="p2">This is another paragraph.</p>
</div>

<script>
const elmnt = document.getElementById("p1"); elmnt.remove();
</script>

-- example with: Removing a Child Node
<div id="div1">
  <p id="p1">This is a paragraph.</p>
  <p id="p2">This is another paragraph.</p>
</div>

<script>
const parent = document.getElementById("div1");
const child = document.getElementById("p1");
parent.removeChild(child);
</script>


-- example with: Replacing HTML Elements 
<div id="div1">
  <p id="p1">This is a paragraph.</p>
  <p id="p2">This is another paragraph.</p>
</div>

<script>
const para = document.createElement("p");
const node = document.createTextNode("This is new.");
para.appendChild(node);

const parent = document.getElementById("div1");
const child = document.getElementById("p1");
parent.replaceChild(para, child);
</script>

-- Not an Array!
A NodeList may look like an array, but it is not.
You can loop through a NodeList and refer to its nodes by index.
But, you cannot use Array methods like push(), pop(), or join() on a NodeList.

A NodeList is a type of DOM object, not a JavaScript native object like an array or a string. It's specifically provided by the DOM API to represent collections of nodes (usually elements) in the DOM tree. While NodeList objects behave in some ways similar to arrays (indexed access, looping), they are not directly compatible with all array methods and do not have the full range of array features.

NodeList: NodeList objects are returned by various DOM methods, such as querySelectorAll and childNodes. They represent collections of DOM nodes and provide a way to access and manipulate elements in the DOM tree. NodeList objects have methods like item(index) to retrieve nodes at specific positions and can be iterated over with loops.

Array: Arrays are native JavaScript objects with built-in methods and properties for manipulating and managing collections of values. They offer a wide range of methods like push(), pop(), map(), filter(), etc., which are not available on NodeList objects by default.

A NodeList in the DOM may appear similar to an array due to its indexed structure and the ability to loop through its elements. However, there are important differences between a NodeList and a true JavaScript array:

Indexing and Looping:
    You can access individual nodes in a NodeList using index notation, just like you would with an array.
    You can loop through a NodeList using methods like for loops or forEach to iterate over its elements.
Array Methods:
    Unlike JavaScript arrays, a NodeList does not have built-in array methods like push(), pop(), join(), map(), filter(), etc.
    Trying to use these array methods directly on a NodeList will result in errors.
Immutability:
    The contents of a NodeList are typically derived from the structure of the DOM. They reflect changes made to the DOM in real-time. As the DOM changes, the NodeList updates accordingly.
Conversion:
    You can convert a NodeList to an array using methods like Array.from(nodeList) or the spread operator [...nodeList]. This allows you to use array methods on the resulting array.

Here's an example of converting a NodeList to an array and using array methods:
    const nodeList = document.querySelectorAll('.myClass'); // Get a NodeList
    const nodeArray = Array.from(nodeList); // Convert NodeList to an array

    nodeArray.push(document.createElement('div')); // Now you can use array methods

In summary, while a NodeList shares some similarities with arrays, it lacks many array-specific methods. If you need to perform array operations on the elements collected by a NodeList, you'll need to convert it to a true JavaScript array first.


----
html alements by dom level versions
The first HTML DOM Level 1 (1998), defined 11 HTML objects, object collections, and properties. These are still valid in HTML5.
Later, in HTML DOM Level 3, more objects, collections, and properties were added.

Property	                    Description	                                                           DOM
document.anchors	            Returns all <a> elements that have a name attribute	                    1
document.applets	            Deprecated	                                                            1
document.baseURI	            Returns the absolute base URI of the document	                        3
document.body	                Returns the <body> element	                                            1
document.cookie	                Returns the document's cookie	                                        1
document.doctype	            Returns the document's doctype	                                        3
document.documentElement	    Returns the <html> element	                                            3
document.documentMode	        Returns the mode used by the browser	                                3
document.documentURI	        Returns the URI of the document	                                        3
document.domain	                Returns the domain name of the document server	                        1
document.domConfig	            Obsolete.	                                                            3
document.embeds	                Returns all <embed> elements	                                        3
document.forms	                Returns all <form> elements	                                            1
document.head	                Returns the <head> element	                                            3
document.images	                Returns all <img> elements	                                            1
document.implementation	        Returns the DOM implementation	                                        3
document.inputEncoding	        Returns the document's encoding (character set)	                        3
document.lastModified	        Returns the date and time the document was updated	                    3
document.links	                Returns all <area> and <a> elements that have a href attribute	        1
document.readyState	            Returns the (loading) status of the document	                        3
document.referrer	            Returns the URI of the referrer (the linking document)	                1
document.scripts	            Returns all <script> elements	                                        3
document.strictErrorChecking	Returns if error checking is enforced	                                3
document.title	                Returns the <title> element	                                            1
document.URL	                Returns the complete URL of the document	                            1