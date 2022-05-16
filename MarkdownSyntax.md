# Mkdocs Syntax

### Syntax:

##### HEADERS 

```html
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
```

##### LISTS >  UNORDERED
```markdown
* Item 1
* Item 2
    * Item 2a
    * Item 2b
```

##### LISTS > ORDERED
```markdown
1. Item 1
2. Item 2
3. Item 3
    * Item 3a
    * Item 3b
```

##### IMAGES

```markdown
![GitHub Logo](/images/logo.png)

Format: ![Alt text](url)
```

##### EMPHASIS

```markdown
*This text will be italic*
_This text also be italic_

**This text will be bold**
__This will also be bold__

*You **can** combine them*
```

##### LINKS

```markdown
http://github.com - automatic!

[GitHub](http://github.com)
```

##### BLOCKQUOTES

```markdown
As Grace Hopper said:

> I've always been more interested
> in the future than in the past.
```
As Grace Hopper said:

> I've always been more interested
> in the future than in the past.


##### BLACKSLASH ESCAPES

```markdown
\*literal asterisks\*
```
\*literal asterisks\*

##### USERNAME @MENTIONS

```markdown
Typing @ symbol, followed by a username, will notify that person.
```

##### FENCED CODE BLOCKS

```markdown
Can you use ``` to create a code block.
```

##### ISSUE REFERENCES

Any number that refers to an Issue or Pull request will be automatically converted into a link 

```markdown
#1
gitbub-flavored-mardown#1
defunkt/github-flavored-markdown#1
```

##### TASK LISTS

```markdown
- [x] this is a complete item
- [ ] this is an incomplete item
- [x] @mentions, #refs, [links](),
**formating**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
```

 [x] this is a complete item
- [ ] this is an incomplete item
- [x] @mentions, #refs, [links](),
**formating**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)

##### TABLES 

You can create tables by assembling a list of words and dividing them with hyphens `-` (for the first row), and then separating each column with a pipe `|`:

```markdown
First Header | Second Header 
------------ | --------------
Content cell 1 | Content cell 2
Content column 1 | Contente column 2
```
First Header | Second Header 
------------ | --------------
Content cell 1 | Content cell 2
Content column 1 | Contente column 2


##### EMOJI

To see a list of every image we support, check out
[Emoji Cheat](www.emoji-cheat-sheet.com).
```markdown
GitHub supports emoji!!!
```
:+1: :sperkles: :camel: :tada: :rocket: :metal:  :octocat:
