<script>
    import { base } from "$app/paths";
</script>

<svelte:head>
    <title>Home</title>
</svelte:head>

<h1>Bobo Lin</h1>

<nav>
    <ul>
        <li><a class="current" href={`${base}/`}>Home</a></li>
        <li><a href={`${base}/projects`}>Projects</a></li>
        <li><a href={`${base}/A2`}>Assignment 2</a></li>
        <li><a href={`${base}/contact`}>Contact</a></li>
        <li><a href={`${base}/resume`}>Resume</a></li>
        <li>
            <a
                href="https://github.com/blin20115"
                target="_blank"
                rel="noreferrer">Github</a
            >
        </li>
    </ul>
</nav>

<p>
    I'm currently a sophomore at MIT studying Math and Computer Science. I'm
    from Chicago, IL and love trying new restaurants, working out, and playing
    Sudoku!
</p>

<img
    src={`${base}/images/IMG_1229.JPG`}
    alt="Here's a picture of me in front of MIT on Mass Ave, with the address,
    77 Massachusetts Avenue!"
    width="600"
    height="450"
/>
