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

### Pseudo-elements and pseudo-classes

CSS introduces the concepts of pseudo-elements and pseudo-classes to permit formatting based on information that lies outside the document tree (e.g. there is no element representing the first line of `<p />`).

**Pseudo-elements** create abstractions about the document tree beyond those specified by the document language.

**Pseudo-classes** classify elements on characteristics other than their name, attributes or content - those that cannot be deduced from the document tree. They might be dynamic (an element may acquire or lose a pseudo-class while user interacts with the document, with exception of `:first-child`).

None of these appear in the document tree. Pseudo-classes are allowed anywhere in selectors while pseudo-elements may only be appended after the last simple selector of the selector.

#### Pseudo-classes

##### :first-child

Matches an element that is the first child element of some other element.

`div > p:first-child` matches any `<p />` that is the first child of `<div />`

##### :link and :visited

* The :link pseudo-class applies for links that have not yet been visited.
* The :visited pseudo-class applies once the link has been visited by the user.

##### :hover, :active and :focus

* The :hover pseudo-class applies while the user designates an element, but does not activate it.
* The :active pseudo-class applies while an element is being activated by the user (e.g. between the times user presses the mouse button and releases it).
* The :focus pseudo-class applies while an element has the focus.

User agents are not allowed to reflow a currently displayed document due to pseudo-class transitions (e.g. different font-size for :active pseudo-class may be ignored).

##### :lang

I am actually not interested in this one.

#### Pseudo-elements

##### :first-line

The :first-line pseudo-element can only be attached to a block container element.

The following properties apply to a :first-line pseudo-element: font properties, color property, background properties, word-spacing, letter-spacing, text-decoration, text-transform and line-height.

##### :first-letter

These are the properties that apply to :first-letter pseudo-elements: font properties, text-decoration, text-transform, letter-spacing, word-spacing (when appropriate), line-height, float, vertical-align (only if float is none), margin properties, padding properties, border properties, color property, background properties.

If an element has :before or :after content, the :first-letter applies to the first letter of the element including that content.

##### :before and :after

They can be used to insert generated content before or after an element's content. They inherit any inheritable properties from the element in the document tree to which they are attached. Non-inherited properties take their initial values.

`p.note:before { content: 'Note: ' }`

## Assigning property values, cascading and inheritance

### Specified, computed and actual values

User agent must assign a value to every property that applies to the target media type for every element. The final value of a property is the result of a four-step calculation:

1. the value is determined through specification - **specified value**
2. then resolved into a value that is used for inheritance - **computed value**
3. then converted into an absolute value if necessary - **used value**
4. finally transformed according to the limitations of the locan environment - **actual value**

#### Specified values

UA must first assign a specified value based on the following mechanisms:

1. if the cascade results in a value, use it. If the value is `inherit`, the specified value is defined in the section below.
2. otherwise, if the property is inherited and the element is not the root of the document tree, use the computed value of the parent element.
3. otherwise, use the property's initial value (indicated in the property definition).

#### Computed values

Specified values are resolved to computed values during the cascade (e.g. URIs are made absolute and `em` and `ex` units are computed to pixel or absolute lengths). Computing never requires UA to render the document.

#### Used values

The used value is the result of taking the computed value and resolving any remaining dependencies into an absolute value.

#### Actual values

The actual value is the used value after any approximations have been applied (e.g. decimal rounding).

### Inheritance

Each property defines whether it is inherited or not. When inheritance occurs, elements inherit computed values.

#### The 'inherit' value

A value of 'inherit' means that for a given element, the property takes as specified value the computed value of the element's parent. The 'inherit' value can be used to enforce inheritance even on properties that are not normally inherited.

### The cascade

Style sheets may have three different origins: author, user and user agent.

To find the value for an element/property combination, the UA must apply the following sorting order:

1. find all declarations that apply to the element and property in question, for the target media type.
2. sort according to importance:
    1. user agent declarations
    2. user normal declarations
    3. author normal declarations
    4. author important declarations
    5. user important declarations
3. sort rules with the same importance and origin by the specificity of selector.
4. sort by order specified: if two declarations have the same weight, origin and specificity, the latter wins.

#### Calculating a selector's specificity

Specificity is calculated as follows:

1. count 1 if the declaration is from a 'style' attribute rather than a rule with a selector, 0 otherwise (= a).
2. count the number of ID attributes in the selector (= b).
3. count the number of other attributes and pseudo-classes in the selector (= c).
4. count the number of element names and pseudo-elements in the selector (= d).

```
* {} /* a=0 b=0 c=0 d=0 -> specificity = 0,0,0,0 */
li:first-line /* a=0 b=0 c=0 d=1 -> specificity = 0,0,0,1 */
ul li /* a=0 b=0 c=0 d=2 -> specificity = 0,0,0,2 */
ul ol+li /* a=0 b=0 c=0 d=3 -> specificity = 0,0,0,3 */
