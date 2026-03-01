<script>
    import { base } from "$app/paths";
    import { page } from "$app/stores";
    import "../style.css";

    let colorScheme = "light dark";
    let root = globalThis.document?.documentElement;

    let localStorage = globalThis.localStorage ?? {};

    if (localStorage.colorScheme) {
        colorScheme = localStorage.colorScheme;
    }

    $: root?.style.setProperty("color-scheme", colorScheme);
    $: localStorage.colorScheme = colorScheme;

    let pages = [
        { url: "/", title: "Home" },
        { url: "/projects", title: "Projects" },
        { url: "/A2", title: "Assignment 2" },
        { url: "/A3", title: "Assignment 3" },
        { url: "/contact", title: "Contact" },
        { url: "/resume", title: "Resume" },
        { url: "https://github.com/blin20115", title: "Github" },
    ];
</script>

<label class="color-scheme-switch">
    Theme:
    <select bind:value={colorScheme}>
        <option value="light dark">Automatic</option>
        <option value="light">Light</option>
        <option value="dark">Dark</option>
    </select>
</label>

<nav>
    <ul>
        {#each pages as p}
            <li>
                <a
                    target={p.url.startsWith("http") ? "_blank" : null}
                    href={p.url.startsWith("http") ? p.url : base + p.url}
                    class:current={p.url === "/"
                        ? $page.url.pathname === base + "/"
                        : !p.url.startsWith("http") &&
                          $page.url.pathname.startsWith(base + p.url)}
                    rel={p.url.startsWith("http") ? "noreferrer" : null}
                >
                    {p.title}
                </a>
            </li>
        {/each}
    </ul>
</nav>

<slot />

<style>
    :global(:root) {
        color-scheme: light dark;
    }

    .color-scheme-switch {
        position: absolute;
        top: 1rem;
        right: 1rem;
        display: inline-flex;
        align-items: center;
        gap: 4px;
        font-size: 80%;
    }

    nav ul,
    nav ul li {
        display: contents;
    }

    nav {
        --border-color: oklch(50% 10% 200 / 40%);
        display: flex;
        margin-bottom: 1em;
        border-bottom: 2px solid var(--border-color);
    }

    nav a {
        flex: 1;
        text-decoration: none;
        color: inherit;
        text-align: center;
        padding: 0.5em;
        border-bottom: 0.4em solid transparent;
    }

    nav a.current {
        border-bottom: 0.4em solid var(--border-color);
        padding-bottom: 0.1em;
    }

    nav a:hover {
        border-bottom: 0.4em solid var(--color-accent);
        background-color: color-mix(in oklch, var(--color-accent), canvas 85%);
        padding-bottom: 0.1em;
    }
</style>
