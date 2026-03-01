<script>
    import { base } from "$app/paths";
    import { page } from "$app/stores";
    import "../style.css";

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
    nav ul,
    nav ul li {
        display: contents;
    }

    nav {
        display: flex;
        margin-bottom: 1em;
        border-bottom: 1px solid oklch(80% 3% 200);
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
        border-bottom: 0.4em solid oklch(80% 3% 200);
        padding-bottom: 0.1em;
    }

    nav a:hover {
        border-bottom: 0.4em solid var(--color-accent);
        background-color: oklch(from var(--color-accent) 95% 5% h);
        padding-bottom: 0.1em;
    }
</style>
