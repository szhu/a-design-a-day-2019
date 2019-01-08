# React Collapsing Element

## Background

In React, sometimes I run into elements with the following structure:

```tsx
<MyCustomButtonComponent href="http://button-link-target">
  <MyFlexboxComponent flexDirection="row" />
</MyCustomButtonComponent>
```

which renders into the DOM as follows:

```tsx
<a href="http://button-link-target">
  <div style={{flexDirection: "row"}} />
</a>
```

but I'd like it to render as

```tsx
<a href="http://button-link-target" style={{flexDirection: "row"}} />
```

The fact that that's not easily possible right now makes me not want to write `MyCustomButtonComponent` and `MyFlexboxComponent` as separate components, but ideally I'd want to keep separate concerns separate.

## Idea

A React component `ElementFragment` that can be used as follows:

```tsx
<ElementFragment className="outer">
  <ElementFragment className="inner">
    <ElementFragment tagName="a" href="http://link-target" />
  </ElementFragment>
</ElementFragment>
```

to produce this DOM tree:

```tsx
<a className="outer inner" href="http://link-target" />
```

Furthermore, components that return a single instance of `ElementFragment` must be able to declare so and allow themselves to not render a DOM element as well:

```tsx
<ElementFragment className="outer">
  <MyInnerElementComponent>
    <MyCustomButtonComponent href="http://link-target" />
  </MyInnerElementComponent>
</ElementFragment>
```

should, with the correct implementations of `MyInnerElementComponent` and `MyCustomButtonComponent`, also return

```tsx
<a className="outer inner" href="http://link-target" />
```
