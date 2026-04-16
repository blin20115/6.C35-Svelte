<script>
    import { base } from "$app/paths";
    export let data = {};
</script>

<article>
    <h2>
        {#if data.url}
            <a href={data.url} target="_blank">{data.title}</a>
        {:else}
            {data.title}
        {/if}
    </h2>
    <img src={`${base}/${data.image}`} alt={data.alt ?? ""} />
    <p>
        {#if data.year}
            <span class="year">{data.year}</span>
        {/if}
        {data.description}
    </p>
</article>

<style>
    article {
        display: grid;
        grid-template-rows: subgrid;
        grid-row: span 3;
    }

    article h2 {
        margin: 0;
    }

    .year {
        font-size: 0.85em;
        font-weight: 600;
        color: oklch(55% 0 0);
        margin-right: 0.4em;
    }
</style>
