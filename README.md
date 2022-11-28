# Svelte Colour Picker

Svelte Colour Picker

### [Demo](https://svelte-colourpicker.vercel.app/)

Installation:

```
npm i svelte-colourpicker
```

Usage:

```html
<script>
    import { ColourPicker } from "svelte-colourpicker"

    let value = "rgba(255, 0, 0, 1)"
</script>

<div>{value}</div>

<ColourPicker bind:value />

<!-- Dark Theme -->
<div data-theme="dark">
    <ColourPicker bind:value />
</div>
```
