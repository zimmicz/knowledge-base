# Sticky
- hybrid between fixed and relative position
- it allows a positioned element to act like it is **relatively positioned** until it is scrolled to a certain threshold after which it **becomes fixed**
- sticky elements are _sticky_ relative to the nearest ancestor with a "scrolling mechanism", which is determined by its ancestor's property
- the offsets are automatically calculated in reference to the nearest scrollport.
- one of the `inset properties (left, right, bottom, top)` has to be defined

> The visual viewport of the [scroll container](https://drafts.csswg.org/css-overflow-3/#scroll-container) (through which the scrollable overflow area can be viewed) coincides with its padding box, and is called the **scrollport**.

## Caveats
- when an element with `position: sticky` is wrapped and is the only child of the wrapper element, it **will not stick**.
	- see https://codesandbox.io/s/css-position-sticky-c1zvc?file=/not_working.html
	- it seems there **needs to be enough siblings to make this work**
- when an element with `position: sticky` is wrapped inside an element with `position: fixed`, it **will not stick**.

## Examples
- [Minimal working sample](https://codesandbox.io/s/css-position-sticky-c1zvc?file=/minimal.html)
- [Not working because there is not enough siblings](https://codesandbox.io/s/css-position-sticky-c1zvc)
- [Working because there is enough siblings](https://codesandbox.io/s/css-position-sticky-c1zvc?file=/wrapped.html)
- [Sticky element inside fixed positioned wrapper](https://codesandbox.io/s/css-position-sticky-c1zvc?file=/fixed.html)