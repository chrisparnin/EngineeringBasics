[Shells](Shells.md#shells) | [Development Environments](PackageManagers.md#development-environments) |  [Git](Git.md#git) | [Virtural Environments](Environments.md#environments) | [Markdown and Editors](MarkdownEditors.md#markdown) | [Programming Languages](Programming.md#programming) | [Task Management](OnlineTools.md#online-tools) | [Specialized Tools](SpecializedTools.md#specialized-tools) 

# Programming

Choose which language you want to try programming in (python/node). Then, We're going to import the product hunt data (posts).

**Practice**: Find the post with the highest number of votes?

What's your first step?  What does the data look like:

If we do `head data/posts--2016-04-01_14-36-24-UTC.csv`, we can see the columns that appear in the data.

```
id;created_at;name;tagline;user_id;user_username;votes_count;comments_count;redirect_url;discussion_url
```

Interesting. There is a `votes_count` column. How can we write a simple program that reads in this CSV file and prints out the post with the most votes?  Option 1: Find a way to sort a list by `votes_count`. Option 2: Loop through each row and keep track of the max vote count and associated post.

## Online Resources

### Cloud Nine

Your development environment in the cloud. You can link your account to a code repository on github and run and execute commands in a development box hosted by c9.

https://c9.io/

### Python Tutor (Debugging and Visualization)

![image](https://cloud.githubusercontent.com/assets/742934/15635634/3b793fec-25b2-11e6-80da-21ea3de7a6d3.png)

http://pythontutor.com/visualize.html#mode=edit

### Python Jupyter

A online notebook for python: http://jupyter.org/

### JSFiddle

A great way to try out javascript in the browser.

http://jsfiddle.net/webdevem/Q8KVC/

### SQL Fiddle

Want to practice a SQL query? SQL Fiddle will allows you to work with a mock database in the cloud.

http://sqlfiddle.com/#!9/dcb16/1
