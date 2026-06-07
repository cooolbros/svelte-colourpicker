<script lang="ts">
    import { ColourPicker } from "$lib"
    import { MediaQuery } from "svelte/reactivity"
    import "../app.css"
    import ThemeToggle from "./ThemeToggle.svelte"

    const media = new MediaQuery("(prefers-color-scheme: dark)")
    let theme: "light" | "dark" = $derived(media.current ? "dark" : "light")

    let value = $state("rgba(255, 0, 0, 1)")

    $effect(() => {
        document.body.dataset.theme = theme
    })
</script>

<svelte:head>
    <title>Svelte Colour Picker</title>
</svelte:head>

<h1>Svelte Colour Picker</h1>

<div class="theme-toggle">
    <ThemeToggle bind:theme />
</div>

<div class="demo">
    <div class="label">{value}</div>
    <ColourPicker bind:value />
</div>

<style>
    h1 {
        font-size: 3rem;
        color: #000000;
        margin-bottom: 2rem;
    }

    :global([data-theme="dark"]) h1 {
        color: #ffffff;
    }

    .theme-toggle {
        margin-bottom: 2rem;
    }

    .demo {
        display: flex;
        align-items: center;
        gap: 1rem;
    }

    .demo .label {
        text-align: center;
        width: 15rem;
        padding: 0.5rem 0;
        border: 1px solid rgba(0, 0, 0, 0.2);
        border-radius: 3px;
    }

    :global([data-theme="dark"]) .demo .label {
        color: #ffffff;
        border: 1px solid rgba(255, 255, 255, 0.2);
    }
</style>
