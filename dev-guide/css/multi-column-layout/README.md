# Multi-column layout

The [Multi-column Layout](https://msdn.microsoft.com/library/Hh771877) allows content to flow into multiple columns, which retain a gap and an optional rule between them. It also makes it possible to vary the number of columns based on the size of the browser window. [CSS Multi-column Layout Module](http://go.microsoft.com/fwlink/p/?LinkId=215567) is a World Wide Web Consortium (W3C) Candidate Recommendation.

A `multi-column` element is an element whose [`column-width`](https://msdn.microsoft.com/library/Hh772211) or [`column-count`](https://msdn.microsoft.com/library/Hh772195) property is not set to `auto`, meaning it acts as a container for multi-column layout. Multi-column layout introduces the *column box*, which is a type of container between the content box and the content. Column boxes contain *rows*, which are ordered in the direction of the multi-column element. Every column box has a *column height* and a *column width*. Adjacent column boxes are separated by a *column gap*, which can optionally contain a *column rule*.


**Linked live examples in this guide will require a browser compatible with unprefixed CSS3 multi-column properties to render correctly.**

## Specifying column width and count


In order to get a multi-column layout up and running, a width for the columns within a multi-column element needs to be specified. Microsoft Edge will display as many columns as it can in the browser window, but a max column count can be set.

### Column width

To specify column width, use the `column-width` property. The `column-width` property specifies the optimal width of the columns in a multi-column element.

The possible values for the property are: 

Value | Description
:----------- | :-----------
auto | Indicates that the optimal column width is determined by the other property values of the multi-column element, such as the `column-count` property. This is the default value.
\<length\> | A relative or absolute length value, as specified in [CSS Values and Units Reference](../length-units-relative-and-absolute).

In this code snippet, the following selector has added the column-width property and set it to 400 pixels. This means Microsoft Edge will fill the browser window with as many columns that have a width of 400 pixels or more.

```css
#multicol1 {
  column-width: 400px;
}
```


In this example, paragraphs will be put into multiple columns. The number of columns depends on the `column-width`. Go ahead and play around with the CSS!

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/wGMEZo)

### Column count


It's simple to set how many columns a multi-column element will have using the `column-count` property. This specifies the optimal number of columns in a multi-column element.

The possible values for the property are:

Value | Description
:---------- | :-----------
auto | Indicates that the number of columns is determined by the values of other property values of the multi-column element, such as the `column-width` property. This is the default value.
\<integer\> | Specifies the number of columns.

The following code snippet shows a selector with an added `column-count` property that is set to "2". This means that Microsoft Edge will fill the browser window with exactly two columns.

```css
#multicol1 {
  column-count: 2;
}
```

Check out this live example!

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/dMGqBx)


### Columns property

Column width and count can also be expressed by using the [`columns`](https://msdn.microsoft.com/library/Hh771860) property. This shorthand value allows you to specify the value of the `column-count` properties of a multi-column element.


The two valid syntax forms for `columns` are:

```css
columns: <column-width> <column-count>;
columns: <column-count> <column-width>;
```

If only an integer is specified, `column-width` is set to `auto` and `column-count` is set to the integer. If only a [length value](http://go.microsoft.com/fwlink/p/?LinkID=204719) is specified, `column-width` is set to the length value and `column-count` is set to `auto`. If only `auto` is specified, both `column-width` and `column-count` are set to `auto`.

This code snippet has a `columns` property that is set to "auto 22em". This means that the multi-column element will have a `column-width` of 22 ems and a `column-count` of `auto`.

```css
#multicol3 {
  columns: auto 22em;
}
```

In this example, the number of columns is set to auto. Resize the window to change the number of 22em wide columns to get a feel for the `columns` property.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/JXGaqx)

## Specifying column gaps and rules

Column gaps and column rules are placed between the columns of a multi-column element, along its entire length. Column gaps create space between columns to facilitate reading. A column rule is drawn in the middle of a column gap, and is only drawn between columns that both have content.

The following properties specify column gaps and rules:

Property | Description
:--------------- | :-----------
[column-gap](https://msdn.microsoft.com/library/Hh772199) | Specifies the width of the gap between columns in a multi-column element. The possible values for this property are: **normal**: The default width of 1 em. **\<length\>**: A relative or absolute length value, as specified in [CSS Values and Units Reference](../length-units-relative-and-absolute ).
[column-rule-color](https://msdn.microsoft.com/library/Hh772202) | Specifies the color for all column rules in a multi-column element. This property can be set to any [supported color value](http://go.microsoft.com/fwlink/p/?LinkId=10129)
[column-rule-style](https://msdn.microsoft.com/library/Hh772204) | Specifies the style for all column rules in a multi-column element. This property accepts the same values as the [`border-style`](http://go.microsoft.com/fwlink/p/?LinkID=208168) property.
[column-rule-width](https://msdn.microsoft.com/library/Hh772206) | Specifies the width of all column rules in a multi-column element. This property accepts the same values as the [`border-width`](http://go.microsoft.com/fwlink/p/?LinkID=215618) property.
[column-rule](https://msdn.microsoft.com/library/Hh772200) | A shorthand value that specifies values for the [`column-rule-color`](https://msdn.microsoft.com/library/Hh772202) properties of a multi-column element. The syntax for this property is as follows:`column-rule: <column-rule-width> <column-rule-style> <column-rule-color>;`


This code snippet shows most of these properties within a selector:

```css
#multicol4 {
  columns: auto 22em;
  column-gap: 2em;
  column-rule-width: 1em;
  column-rule-style: solid;
  column-rule-color: black;
}
```

In the CSS of this example, we've set a gap and rule. The gap is 2em wide, and the rule is 1em wide. This results in a a 1em wide line with a .5em wide gap on either side of it.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/Wwrgmp)

This example could also be expressed using the [`column-rule`](https://msdn.microsoft.com/library/Hh772200) shorthand property:

```css
#multicol4 {
  columns: auto 22em;
  column-gap: 2em;
  column-rule: 1em solid black;
}
```

## Specifying column breaks


You can specify when content should break between columns. This prevents content from breaking in the middle of paragraphs, sections, and so on. The concept of column breaks is similar to page-breaks when printing.

The following properties control column breaks:

Property | Description
:----------| :------------
[break-before](https://msdn.microsoft.com/library/Hh772189) | Specifies the column-break behavior that precedes a content block in a multi-column element. This property accepts the same values as the [`page-break-before`](https://msdn.microsoft.com/library/ms530844) property, plus the following values- **page**: Always force a page break before the generated box. **column**: Always force a column break before the generated box. **avoid-page**: Avoid a page break before the generated box. **avoid-column**: Avoid a column break before the generated box.
[break-after](https://msdn.microsoft.com/library/Hh772187) | Specifies the column-break behavior that follows a content block in a multi-column element. This property accepts the same values as the [`page-break-after`](https://msdn.microsoft.com/library/ms530842) property, plus the following values- **page**: Always force a page break before the generated box. **column**: Always force a column break before the generated box. **avoid-page**: Avoid a page break before the generated box. **avoid-column**: Avoid a column break before the generated box.
[break-inside](https://msdn.microsoft.com/library/Hh772193) | Specifies the column-break behavior that occurs within a content block in a multi-column element. This property accepts the same values as the [`page-break-inside`](https://msdn.microsoft.com/library/Cc304067) property, plus the following values- **avoid-page**: Avoid a page break before the generated box. **avoid-column**: Avoid a column break before the generated box.

This code snippet highlights `break-before` and `break-inside`:

```css
#multicol5 {
	column-count: 3;
	column-gap: 2em;
	column-rule-width: 1px;
	column-rule-style: solid;
	column-rule-color: black;
}
#multicol5 h2 {
	break-before: column;
	margin-top: 2em;
}
#multicol5 blockquote {
	break-inside: avoid-column;
}
```

In this example, all [`h2`](http://go.microsoft.com/fwlink/p/?LinkID=215639) elements are preceded by a column break as well as a 2em margin, and no column breaks can appear within a [`blockquote`](https://msdn.microsoft.com/library/ms535202) element. 

Check out `break-before` and `break-inside` in this example!

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/pygOGW)

In this example, we do a column break before h2s . If this break wasn't here, the h2 would appear in the first column.
We also do a `break-inside: avoid-column`. As you can see, this keeps the blockquote all in one column. Try removing the CSS for "#multicol5 blockquote" to see the blockquote without a break.

## Specifying column span


If you want a content block to span across several columns, the [`column-span`](https://msdn.microsoft.com/library/hh772209) property is the way to do it. An element that has been spanned across several columns effectively acts as a break between the content before and the content after the span.

The `column-span` property sets the number of columns that a content block spans in a multi-column element. 
It has two possible values:

Value | Description
:------------ | :------------
all | The content block spans all columns on a page. All content that is declared before the content block is shown before the content block.
"1" | This is the default value. The content block does not span multiple columns.


The following code snippet shows an example of spanning:

```css
#multicol6 {
  columns: auto 22em;
  column-gap: 2em;
  column-rule-width: 1em;
  column-rule-style: solid;
  column-rule-color: black;
}
#multicol6 h2 {
  column-span: all;
  background: dodgerblue;
}
```

In this case, all `h2` elements span all columns, and have a blue background.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/oxbPKr)

## Balancing column content


Let's say you want to make all of your columns approximately the same size in order to keep everything neat. There's a way to do that thanks to the [`column-fill`](https://msdn.microsoft.com/library/Hh772197) property! Without this property, columns are filled sequentially and have different lengths.

The `column-fill` property has two possible values:

Value | Description
:--------- | :-----------
balance | Columns are filled sequentially such that the column heights are as balanced as possible, depending on other column property values.
auto | This is the default value. Columns are filled sequentially such that the columns might differ in length, depending on other column property values.

Here is a code snippet showing `balance`:

```css
#multicol7 {
  columns: 4;
  height: 100px;
  column-fill: balance;
}
```

In this case, the `column-fill` property has been set to `balance`, which means that column lengths are as balanced as possible.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/bpExOB)

## API reference

[Multi-column Layout](https://msdn.microsoft.com/library/Hh771877)

## Demos

[CSS Multi-column layout CodePen collection](https://codepen.io/collection/XgPGpm/)


## Specification

[CSS Multi-column Layout Module](http://go.microsoft.com/fwlink/p/?LinkID=215567)
