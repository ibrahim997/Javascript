# Lesson 2

## Including Javascript in Your Web Page

Previously, you learned that Javascript programs are pased to the browser along with page content. But how exactly is that achieved? Two basic methods associate Javascript code with a HTML page, both of which use the <script></script> element introduced in Lesson 1.

One method is to include the Javascript statements directly into the HTML file, just like you did previously:
```javascript
<script>
  ... Javascript statements are written here...
</script>
```
A second method and more favourable method is to include your code in a separate file and use the <script> element to include that file by name using the scr (source) attribute:
```javascript
<script src='mycode.js'></script>
```
The file *mycode.js* contains the Javascript statements, but if youare Javascript file is not in the same folder as the calling script, you can also add a (relative or absolute) path to it:
```javascript
<script src='path/to/mycode.js'></script>
```
or
```javascript
<script src='http://www.example.com/path/to/mycode.js'></script>
```



