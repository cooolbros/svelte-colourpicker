<script lang="ts">
    export let theme: "light" | "dark"
</script>

<button
    class="container"
    style:--background={theme == "light" ? "rgb(255, 220, 60)" : "rgb(25, 80, 150)"}
    on:click={() => (theme = theme == "light" ? "dark" : "light")}
    on:mouseup|stopPropagation
>
    <div class="switch" style:--translate={theme == "light" ? "0px" : "32px"}>
        {#if theme == "light"}
            <!-- https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Alight_mode%3AFILL%401%3Bwght%40100%3BGRAD%400%3Bopsz%4024 -->
            <svg xmlns="http://www.w3.org/2000/svg" height={24} width={24} fill="#000000">
                <path
                    d="M12 15.7q-1.55 0-2.625-1.075T8.3 12q0-1.55 1.075-2.625T12 8.3q1.55 0 2.625 1.075T15.7 12q0 1.55-1.075 2.625T12 15.7ZM2 12.35q-.15 0-.25-.1t-.1-.25q0-.15.1-.25t.25-.1h2.65q.15 0 .25.1T5 12q0 .15-.1.25t-.25.1Zm17.35 0q-.15 0-.25-.1T19 12q0-.15.1-.25t.25-.1H22q.15 0 .25.1t.1.25q0 .15-.1.25t-.25.1ZM12 5q-.15 0-.25-.1t-.1-.25V2q0-.15.1-.25t.25-.1q.15 0 .25.1t.1.25v2.65q0 .15-.1.25T12 5Zm0 17.35q-.15 0-.25-.1t-.1-.25v-2.65q0-.15.1-.25T12 19q.15 0 .25.1t.1.25V22q0 .15-.1.25t-.25.1ZM6.575 7.025l-1.55-1.5q-.1-.1-.1-.238 0-.137.1-.262.125-.125.25-.125t.25.125L7.05 6.55q.125.125.125.25t-.1.25q-.125.125-.25.112-.125-.012-.25-.137Zm11.9 11.95L16.95 17.45q-.125-.125-.125-.25t.125-.25q.1-.125.225-.113.125.013.25.138l1.55 1.5q.1.1.1.237 0 .138-.1.263-.125.125-.25.125t-.25-.125ZM16.95 7.05q-.125-.1-.113-.225.013-.125.138-.25l1.5-1.55q.1-.1.237-.1.138 0 .263.1.125.125.125.25t-.125.25L17.45 7.05q-.125.125-.25.125t-.25-.125ZM5.025 18.975q-.125-.125-.125-.25t.125-.25L6.55 16.95q.125-.125.25-.125t.25.125q.1.075.088.213-.013.137-.113.262l-1.5 1.55q-.125.125-.25.125t-.25-.125Z"
                />
            </svg>
        {:else}
            <!-- https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Adark_mode%3AFILL%401%3Bwght%40400%3BGRAD%400%3Bopsz%4024 -->
            <svg xmlns="http://www.w3.org/2000/svg" height={24} width={24} fill="#ffffff">
                <path
                    d="M12.075 19.7q-3.2 0-5.45-2.25T4.375 12q0-2.825 1.787-4.938Q7.95 4.95 10.625 4.425q-.35.7-.55 1.475-.2.775-.2 1.6 0 2.8 1.95 4.75 1.95 1.95 4.75 1.95.825 0 1.6-.2.775-.2 1.45-.55-.5 2.675-2.613 4.463Q14.9 19.7 12.075 19.7Z"
                />
            </svg>
        {/if}
    </div>
</button>

<style>
    .container {
        text-align: left;
        width: 3.5rem;
        height: 1.5rem;
        padding: 2px;
        background: var(--background);
        border: none;
        border-radius: calc((1.5rem + 4px) / 2);
        outline: none;
        box-sizing: content-box;
    }

    .switch {
        width: 1.5rem;
        height: 1.5rem;
        display: inline-block;
        transform: translate(var(--translate));
        transition: 100ms ease-in-out;
    }

    .switch svg {
        transform: scale(0.9);
    }
</style>
