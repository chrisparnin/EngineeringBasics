# Markdown

Is a plain text format that can be used to express stylized text rendered as html (or even pdf). It is commonly used in online tools such as Github to make it easier to write reports or documentation. You can mix and match html with markdown, but there are limits, e.g. including a link to a css file.

How about an example. The following markdown syntax, would appear as follows:

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

### Tables

There are many different "flavors" of markdown. [Github-flavored markdown](https://help.github.com/articles/organizing-information-with-tables/) supports "tables". Which can be nice to report data results:

```
| Parameters     | 5% tfidf scores - 34 nodes | 10 % tfidf score - 34 nodes | original result for 2 GB - 34 nodes |
| ------------- |:-------------:|:-------------:|:-------------:|
| Vocabsize | 19529 | 39172 | 262144 |
| Total Token size for training | 256469820 | 238648536 | 211167796 |
| Total documents size for training | 209313401 | 209313401 | 7706477 |
| Total Time | 17 min | 24 min | 33 min |
| Total used memory     | 3.5 GB | 4.5 GB | 3.1 GB |
| Memory usage per node | 100 MB | 250 MB | 100 MB |
| Input per node | 5 GB | 6 GB | 3GB |
```
| Parameters     | 5% tfidf scores - 34 nodes | 10 % tfidf score - 34 nodes | original result for 2 GB - 34 nodes |
| ------------- |:-------------:|:-------------:|:-------------:|
| Vocabsize | 19529 | 39172 | 262144 |
| Total Token size for training | 256469820 | 238648536 | 211167796 |
| Total documents size for training | 209313401 | 209313401 | 7706477 |
| Total Time | 17 min | 24 min | 33 min |
| Total used memory     | 3.5 GB | 4.5 GB | 3.1 GB |
| Memory usage per node | 100 MB | 250 MB | 100 MB |
| Input per node | 5 GB | 6 GB | 3GB |

### Editors

If you're still opening and editing files in Notepad.exe, let's show you a better way.

When editing markdown and code scripts, features such as syntax highlighting, autocomplete, and advanced find and replace tools are essential!

##### Markdown editors

* Online: Github's built in editors are great for simple Markdown editing!
* Online: Also see: http://dillinger.io/
* Mac: [MacDown](http://macdown.uranusjr.com/)
* IPad: [ByWord](https://itunes.apple.com/us/app/byword/id482063361?mt=8)
* Windows: [MarkdownPad 2](http://markdownpad.com/download.html)
