---
title: Advanced Markdown Features
author: Kristian
date: 2022-09-23 21:16:00 +0200
categories: [Guide, Information]
tags: [it, software, html, markdown]
---
# Markdown skills

## Common
- create headers using `# title`
<details>
<summary>Example</summary>

  - `# h1`
  - `## h2`
  - `### h3`
  - `#### h4`
  - `##### h5`
  - `###### h6`

</details>

- Emphasis ex bold, italic text

<details>
<summary>Example</summary>

**Looks:**
  - **This is bold text**
  - **This is bold text**
  - *This is italic text*
  - *This is italic text*
  - ~~Strikethrough~~

**Code:**
```markdown
    - **This is bold text**
    - __This is bold text__
    - *This is italic text*
    - _This is italic text_
    - ~~Strikethrough~~
```
</details>

- Blockquotes using `>` can be indented using multiple `>>`,`>>>`
- Inline code using \`CODE\`
- Multiline code using \```, able to set syntax highlightning by added name of language after the \```CODE ex \```yaml
- Images

<details>
<summary>Example</summary>

<img src="https://octodex.github.com/images/minion.png" alt="Minion" width="200"/>


**Code:**
```html
<img src="https://octodex.github.com/images/minion.png" alt="Minion" width="200"/>
```
</details>

- Links

<details>
<summary>Example:</summary>

**Example:**
  - This is [an example](http://example.com/ "Title") inline link.
  - [This link](http://example.net/) has no title attribute.

**Code:**
```md
This is [an example](http://example.com/ "Title") inline link.
[This link](http://example.net/) has no title attribute.
```
</details>

- Markdown provides backslash escapes for the following characters:

<details>
<summary>Show The characters:</summary>
  - \   backslash
  - `   backtick
  - - asterisk
  - _   underscore
  - {}  curly braces
  - []  square brackets
  - ()  parentheses
  - \# hash mark
  - + plus sign
  - - minus sign (hyphen)
  - .   dot
  - !   exclamation mark
</details>

## Advanced
Awesome small tricks for the advance usage of markdown

- Create a bigger font size without creating a header: `<font size="18">**Awesome Document:**</font>`
- Create a collapsable with a "title":
<details>
<summary>Example</summary>

<details>
<summary>Details</summary>

**TEXT INSIDE DETAILS**

- This is just some text inside the details part

</details>

**Code:**
```html
<details>
<summary>Details</summary>

**TEXT INSIDE DETAILS**
- This is just some text inside the details part
</details>
```
</details>
