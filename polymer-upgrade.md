---
theme: "night"
customTheme : "me"
transition: "slide"
highlightTheme: "darkula"
title: "polymer upgrade"
---

## Polymer 2 Upgrade

---

## What?

| &nbsp;           | <small>we are here | <small>planned to <br>migrate here |
| ---------------- | ------------------ | ---------------------------------- |
| Polymer          | 1                  | 2                                  |
| webcomponents.js | 0.7                | 1.0                                |
| shadow DOM       | V0                 | V1                                 |
| WCT              | 4.0                | 6.0                                |
| Polymer Elements | 1.0                | 2.0                                |

---

## Strategy

For large applications, where you have written many of your own reusable elements, you may want to upgrade elements individually to hybrid mode.

<small>https://polymer-library.polymer-project.org/2.0/docs/upgrade

---

## Plan

Polymer 1 **>** `Hybrid Mode` **>** Polymer 2

--

### Polymer 1

  - identify 1<sup><small>st</small></sup> and 2<sup><small>nd</small></sup> level dependency components
  - convert P1 components to hybrid mode
  - test and deploy to DEV > PROD

--

### Polymer 2

  - hybrid components works with legacy syntax
  - convert hybrid to P2 components / ES6 syntax
  - Done!!

---

## Hybrid Elements?

- 1.x-style Polymer() function call
- 2.x-style DOM template
- runs under both Polymer 1.x and 2.x

<small>*Polymer 2 provides a backwards-compatible API for hybrid elements.</small>

---

## How to upgrade?

---

### DOM Module

- use **id** instead of *name* or *is*
- **style** must be placed inside template

```html
<!-- before -->
<dom-module name="el-one">
  <style></style>
  <template></template>
</dom-module>
```

```html
<!-- After -->
<dom-module id="el-one">
  <template>
    <style></style>
  </template>
</dom-module>
```

---

### Content Element

replace content with slot

```html
<!-- before -->
<dom-module name="el-one">
  <template>
    <content select=".className"></content>
    <content></content>
  </template>
</dom-module>

<!-- x.html -->
<el-one>
  <span class="className">content 1</span>
  <span>content 2</span>
</el-one>
```

--

### Content Element

replace content with slot

```html
<!-- After -->
<dom-module id="el-one">
  <template>
    <slot name="title"></slot>
    <slot></slot>
  </template>
</dom-module>

<!-- x.html -->
<el-one>
  <span slot="title">content 1</span>
  <span>content 2</span>
</el-one>
```

---

### Shadow DOM styles

- Replace ::content selectors with ::slotted() selectors
- Remove /deep/ and ::shadow selectors
- Remove :root selectors

```css
/* before */
:root{}
::content > .class

/* after */
:host > * {}
::slotted(.class)
```

---

### Custom property syntax

```css
/* before */
color: var(--special-color,--default-color);
@apply(--my-mixin);

/* After */
color: var(--special-color, var(--default-color));
@apply --my-mixin;
```

---

### Wrap custom-style elements

```html
<!-- before -->
<style is="custom-style">

/* after */
<custom-style>
  <style is="custom-style">
</custom-style>
```

---

### ing-base.html

- will be replaced by ing-common-styles.html
- and component specific shared styles

---

### what else?

- Life cycle changes
- Deprecated APIs
- and more...

<small>please refer ing wiki

---

## How to test?

- Google Way
- ING Way ?!

--

### Google Way

- using Polymer CLI
- install multiple versions of dependencies called variants
- fix the breaking changes
- `polymer serve` and `polymer test` runs both versions at the same time from different ports

<small>https://polymer-library.polymer-project.org/2.0/docs/devguide/hybrid-elements#dependency-variants</small>

--

### ING Way

- create a folder and copy source code from p1 folder
- replace Polymer 1 related files with polymer 2
- fix the breaking changes
- test the component in polymer 2
- copy the code changes to p1 folder
- test again
- web view, then need to be tested in native App using Perfecto

---

## Need more info?

Check

- Polymer upgrade - ING wiki page
- Polymer 2 upgrade doc. from polymer

---

# Fin
