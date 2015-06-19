# README

This is the GitHub repository for Microsoft Edge documentation for http://dev.modern.ie

At the mooment, both MS Edge and IE developer content still live in MSDN Library at https://msdnstage.redmond.corp.microsoft.com/en-us/library/hh772401(v=vs.85).aspx
We are working to port the MS Edge-related topics and resources here, as well as exclusively author any new content (e.g., extensions) here.

TODO: 
* Contributing guide
* License

## Instructions / Format for adding new Docs and Links

  - Docs are grouped by folders
  - A folder can contain more folders or a readme.md
  - One .md file per folder
  - Folder/directory names should be dash-separated (ie. f12-tools) as they will be directly used for documentation URLs on the Microsoft Edge Dev site ---- NOT underscore (ie. f12_tools) or PascaleCase/camelCase (ie. f12Tools). 
  - Links should be formatted as: ../Perfomance/  (not ../Perfomance/ReadMe.md)
  - Section headers should use a standard syntax of a space after hashes, formatted as  ## Section Heading *(not ##Section Heading)*. Otherwise markdown is not being parsed correctly when pulled into the Microsoft Edge Dev site.
  - For a guide to writing GitHub Markdown: https://guides.github.com/features/mastering-markdown/
:octocat:
  - *Include a License.md in your Repo*
  >[Info about Licensing on GitHub](https://help.github.com/articles/open-source-licensing/)

Example: 
>*Copyright (c) Microsoft Corporation. All rights reserved.*

>*Licensed under the Apache License, Version 2.0 (the "License"); you may not use these files except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0*

>*Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.*

# Styling

The following sections you an overview of what elements have been styled up for documentation in the developer portal site.

## Header elements

Only the h3 and the h4 elements have a faint separator line underneath them. h1 (use for main title only) and h2 are simply larger text.

### Subsection header

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

#### An h4 tag will lend you better visual hierarchy than bolding some text.

Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

#### Also a small header

Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## Other text elements

These other text elements have styling available:

* Unordered lists
* Have regular bullets
   * You can also nest bullets
* Pretty standard

1. Ordered lists
2. Have regular ol' western-style numbering.
3. Use these only when a list truly has order.

_________________________

Horizontal rules are available to use. Would suggest using sparingly to keep things from getting overly cluttered with lines.
Do not use horizontal rules consecutively with heading tags; some of them are already styled with lines for visual hierarchy.

## Displaying code

You can use inline `code` Markdown syntax (with the backticks).

Or you can display blocks of code like so:

```
body {
	background: #fff;
}
```

## Tables

| You can     | use headers | on tables    |
|-------------|-------------|-------------:|
| Left-aligned| Unless a #  | 456          |
| Text value  | More text   | $0.00        |

## Notes

Use notes sparingly. They are bright color blocks intended to call out don't-miss-it information.

We have three different versions of notes currently styled:

* `>note` (default styling)
* `>note.warning`
* `>note.error`

Respectively, those look like:

![Note patterns](media/notes.png)

### How they work

You precede a single line of Markdown with the `>note.*` syntax, like so:

```
>note.warning Hello yes I am a warning note that has been automagically created. My text may wrap to more than one line when the Markdown is parsed, but I am restricted to putting all my information onto one long line in the Markdown itself.
```

No closing tag is needed. If you try to "wrap" this custom syntax around multiple lines, **it will not work!**

But how do the titles ("Note", "Warning", "Error") get inserted into the note output? The custom Markdown tag actually does a lot
more than you might think. By using `>note.warning`, you are creating a div with class `.note--warning`, and adding to that div a
title `"Warning"`.

If you were to do `>note.pineapple`, you would get a div with class `.note--pineapple`, and a title of "Pineapple". Because we have
not explicitly styled `.note--pineapple`, the styling would simply match the default note styling.

## Images
File an issue if you really need a custom note class to be styled to not look "default". For the most part, though, you should
be using the types provided so that the documentation doesn't turn into a smorgasbord of color.

Images (like the one above) are styled to be fluid, i.e. they will scale proportionally and will never be displayed bigger
than the element containing the documentation article. Currently, that containing element spans up to 875px wide at its
largest, so that or similar should probably be the largest image size you use.
