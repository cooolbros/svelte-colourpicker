# Svelte Colour Picker

```html
<script>
    let value = "rgba(255, 0, 0, 1)"
</script>

<div>{value}</div>

<ColourPicker bind:value />

<!-- Dark Theme -->
<div data-theme="dark">
    <ColourPicker bind:value />
</div>
```
