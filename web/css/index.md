# CSS

[The official definition](https://www.w3.org/TR/CSS/#css)

## Selectors

### Universal selector

`*` matches the name of any element type
`*.warning === .warning`

### Type selector

Matches every instance of the element type in the document tree.
`h1 { font-family: serif }` matches all `<h1 />` elements.

### Descendant selectors

`h1 em { color: blue }` matches all `<em />` inside `<h1 />`
`div * p` matches a `<p />` that is a grandchild or later descendant of `<div />`

### Child selectors

`body > p` matches all `<p />` that are children of `<body />`

### Adjacent sibling selectors

`p + ul { margin-top: 1rem }` matches `<ul />` that immediately follows `<p />`

### Attribute selectors

`[att]` matches when the element has `att` attribute, no matter its value

```
h1[title] { color: blue }
```

`[att=val]` matches when the element has `att` attribute with the value `val`

```
span[class=example] { color: blue }
span[id=hello][class=world] { color: blue }
```

`[att~=val]` matches when the element has `att` attribute with white-space separated list of words, one of which is exactly `val`

```
a[rel~=copyright] { color: blue }
```

`[att|=val]` matches when the element has `att` with the value `val` or with the value beginning with `val-`

#### Class selectors

**Note:** `div.value === div[class~=value]`

To match a subset of class values, each value must be preceeded with `.`:

```
p.marine.pastoral { color: blue }
```

### ID selectors

Document languages may contain attributes that are declared to be of type ID. No two ID attributes can have the same value. In HTML, all ID attributes are called `id`.

**ID selectors have a higher specificity than attribute selectors.**

```
h1#chapter1 { text-align: center }
```

TODO: https://www.w3.org/TR/CSS22/selector.html#pseudo-elements
