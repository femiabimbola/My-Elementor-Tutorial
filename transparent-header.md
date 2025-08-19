# Having Transparent Header

Design your hero section first. <BR/>
Then design your header with transparent header and set the height to 80px<br/>
Move the hero section up by -80px at the bottom <br/>
Set the z-index of the header to 9

Copy and pass this code to the custom header

```css
-- CSS Code Snippet --
/* Sticky Effect Settings */
.elementor-sticky--effects.sticky-menu {
  background: black !important;
}
```

Then set the sticky effect to top and set the <b>_effect offset to 100_</b> <br/>
Put the CSS classes as <b>sticky-menu</b>
