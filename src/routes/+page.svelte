<script lang="ts">
    import { browser } from "$app/environment"
    import { ColourPicker } from "$lib"
    import { onDestroy, onMount } from "svelte"
    import "../app.css"
    import ThemeToggle from "./ThemeToggle.svelte"

    let theme: "light" | "dark" = "light"

    let media: MediaQueryList

    let value = "rgba(255, 0, 0, 1)"

    onMount(() => {
        media = matchMedia("(prefers-color-scheme: dark)")
        theme = media.matches ? "dark" : "light"
        media.addEventListener("change", change)
    })

    onDestroy(() => {
        media?.removeEventListener("change", change)
    })

    function change(e: MediaQueryListEvent) {
        theme = e.matches ? "dark" : "light"
    }

    $: theme && setTheme()

    function setTheme() {
        if (browser) {
            document.body.dataset.theme = theme
        }
    }
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
