# How to write Java documentation
These are rules for writing documentation comments and is based on [this](https://www.oracle.com/technetwork/java/javase/documentation/index-137868.html) article from the Oracle Technology Network.

> **Note**: The term _Documentation Comments_ are used to denote comments enclosed in `/** ... */` which are processed by the `javadoc` tool for generating API documentation.

## Overview
The following is an example of a typical documentation comments (refer to this example while reading the documentation):

```
/**
 * Returns an Image object that can then be painted on the screen. 
 * The url argument must specify an absolute {@link URL}. The name
 * argument is a specifier that is relative to the url argument. 
 * <p>
 * This method always returns immediately, whether or not the 
 * image exists. When this applet attempts to draw the image on
 * the screen, the data will be loaded. The graphics primitives 
 * that draw the image will incrementally paint on the screen. 
 *
 * @param  url  an absolute URL giving the base location of the image
 * @param  name the location of the image, relative to the url argument
 * @return      the image at the specified URL
 * @see         Image
 */
 public Image getImage(URL url, String name) {
        try {
            return getImage(new URL(url, name));
        } catch (MalformedURLException e) {
            return null;
        }
 }
```

Notice the following:
* The documentation in enclosed between `/** ... */` and each following line starts with a single asterisk. The code is indented to aligh with these asterisks.
* The documentation is divided into two sections - description section and the block tags section.

> **Tags:** Tags are predefined keywords prefixed with an `@` symbol and convey special meaning to the `javadoc` tool. There are two types of tags - inline tags and block tags.
>* **Inline Tags:** These tags can appear anywhere in the documentation comments, in either section. These tags may also appear in between lines. For example, `@link` tag.
>* **Block Tags:** These tags define a block (think of it like a paragraph) of text. By convention these tags only appear in the block tags section. For example `@param` or `@see` tags.

The resulting HTML render of the above documentation comments is as follows:

<pre style="font-family='Consolas'">
getImage
public Image getImage(URL url,
             String name)
Returns an Image object that can then be painted on the screen. The url argument must specify an absolute URL. The name argument is a specifier that is relative to the url argument.

This method always returns immediately, whether or not the image exists. When this applet attempts to draw the image on the screen, the data will be loaded. The graphics primitives that draw the image will incrementally paint on the screen.

<b>Parameters:</b>
url - an absolute URL giving the base location of the image.
name - the location of the image, relative to the url argument.

<b>Returns:</b>
the image at the specified URL.

<b>See Also:</b>
Image
</pre>

## 