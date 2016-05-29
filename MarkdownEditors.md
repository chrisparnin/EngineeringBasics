# Markdown

Is a plain text format that can be used to express stylized text rendered as html (or even pdf). It is commonly used in online tools such as Github to make it easier to write reports or documentation.

So the following markdown syntax, would appear as follows:

```
##### Example Header (like \<h5\>Header\</h5\>)

Paragraphs are separated by a blank line.  A hard break can be created by adding two spaces after a sentance.

2nd paragraph. *Italic*, **bold**, and `monospace` (inline code). 
```

##### Example Header (like \<h5\>Header\</h5\>)

Paragraphs are separated by a blank line.  A hard break can be created by adding two spaces after a sentance.

2nd paragraph. *Italic*, **bold**, and `monospace` (inline code). 

### Lists, Blockquotes, Hrefs, and Images

You can do more advanced things, such as creating lists
```
Itemized lists look like:

  * this one
  * that one
  * the other one

> Block quotes are
> written like so.

Hrefs have an anchor in brackets [] and (link in parens): [Markdown format](https://daringfireball.net/projects/markdown/)

Embedded Image: ![img](http://jsforcats.com/images/customers3.png)
```
Itemized lists look like:

  * this one
  * that one
  * the other one

> Block quotes are
> written like so.

Hrefs have an anchor in brackets [] and (link in parens): [Markdown format](https://daringfireball.net/projects/markdown/)

Embedded Image: ![img](http://jsforcats.com/images/customers3.png)

### Code

```
Code (`inline code`):

    print “Code is just indented four spaces”;
```

Code (`inline code`):

    print “Code is just indented four spaces”;

You can also create code using "code fences" 

    ```python
    n = 50 # We want to find prime numbers between 2 and 50

    print sorted(set(range(2,n+1)).difference(set((p * f) for p in range(2,int(n**0.5) + 2) for f in range(2,(n/p)+1))))
    ```

```python
n = 50 # We want to find prime numbers between 2 and 50

print sorted(set(range(2,n+1)).difference(set((p * f) for p in range(2,int(n**0.5) + 2) for f in range(2,(n/p)+1))))
```

