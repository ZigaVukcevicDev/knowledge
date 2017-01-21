## CSS

### BEM

Blocks, Elements and Modifiers

#### Block

Standalone entity that is meaningful on its own.
Examples: `header, container, menu, checkbox, input`

#### Element

A part of a block that has no standalone meaning and is semantically tied to its block.
Examples: `menu item, list item, checkbox caption, header title`

#### Modifier

A flag on a **block** or **element**. Use them to change appearance or behavior.
Examples: disabled, highlighted, checked, fixed, size big, color yellow`

Usage:

The naming rules tell us to use `block--modifier` syntax.

__HTML__

```
<button class="button button--state-success">
	Success button
</button>
<button class="button button--state-danger">
	Danger button
</button>
```

__CSS__

```
.button { // rules for button }
.button--state-success { // rules for state-success modifier }
.button--state-danger  { // rules for state-danger modifier }
```

If there would be an `element` involved, we would use `block__elem--modifier` syntax.

How to correctly work with grandchildren selectors:

__HTML__

```
<div class="card">
    <div class="card__header">
        <h2 class="card__title">Title text here</h2>
    </div>
    <div class="card__body">
        <img class="card__img" src="some-img.png">

        <p class="card__text">Lorem ipsum dolor sit amet, consectetur</p>
        <p class="card__text">Adipiscing elit.
            <a href="/somelink.html" class="card__link">Pellentesque amet</a>
        </p>
    </div>
</div>
```

Don't use `card__body__text__link` as this will quickly get out of hand.