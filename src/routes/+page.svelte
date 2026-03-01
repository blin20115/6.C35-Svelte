<script>
    import { base } from "$app/paths";
    import projects from "$lib/projects.json";
    import Project from "$lib/Project.svelte";
    import reading from "$lib/reading.json";
    import ReadingItem from "$lib/ReadingItem.svelte";
</script>

<svelte:head>
    <title>Home</title>
</svelte:head>

<h1>Bobo Lin</h1>

<p>
    I'm currently a sophomore at MIT studying Math and Computer Science. I'm
    from Chicago, IL and love trying new restaurants, working out, and playing
    Sudoku!
</p>

<img
    src={`${base}/images/IMG_1229.JPG`}
    alt="Here's a picture of me in front of MIT on Mass Ave, with the address, 77 Massachusetts Avenue!"
    width="600"
    height="450"
/>

<h2>Latest projects</h2>
<div class="projects highlights">
    {#each projects.slice(0, 3) as p (p.title)}
        <Project data={p} />
    {/each}
</div>

<h2>What I’m Reading</h2>
<div class="reading">
    {#each reading as item (item.title)}
        <ReadingItem data={{ ...item, image: `${base}${item.image}` }} />
    {/each}
</div>
