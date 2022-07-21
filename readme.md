
### yep

Prints classes for supported features.

	@include yep($features...) { ... }

### nope

Prints classes for unsupported features and unavailable Javascript.

	@include nope($features...) { ... }

### Example

Sass input:

```scss
.my-selector {
	@include yep(translate3d, opacity) {
		transform: translate3d(0, 100px, 0);
		opacity: 0;
	}
	@include nope(translate3d, opacity) {
		top: 100px;
		display: none;
	}
}
```

CSS output:

```css
.translate3d.opacity .my-selector {
  transform: translate3d(0, 100px, 0);
  opacity: 0;
}
.no-js .my-selector,
.no-translate3d .my-selector,
.no-opacity .my-selector {
  top: 100px;
  display: none;
}
```