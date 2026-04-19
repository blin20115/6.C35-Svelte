<script>
    import * as d3 from "d3";

    let width = 400;
    let height = 300;

    let margin = { top: 80, right: 20, bottom: 50, left: 60 };
    let innerWidth = width - margin.left - margin.right;
    let innerHeight = height - margin.top - margin.bottom;

    export let data = [];

    $: xScale = d3
        .scaleBand()
        .domain(data.map((d) => d.label))
        .range([0, innerWidth])
        .padding(0.2);

    $: yScale = d3
        .scaleLinear()
        .domain([0, d3.max(data, (d) => d.value) || 1])
        .range([innerHeight, 0]);

    $: colorScale = d3
        .scaleOrdinal(d3.schemeTableau10)
        .domain(data.map((d) => d.label));

    $: maxBar = d3.greatest(data, (d) => d.value);

    let selectedIndex = -1;

    function toggleBar(index, event) {
        if (!event.key || event.key === "Enter") {
            selectedIndex = index;
        }
    }

    let xAxis, yAxis;

    $: if (xAxis && yAxis) {
        d3.select(xAxis).call(d3.axisBottom(xScale));
        d3.select(yAxis).call(
            d3
                .axisLeft(yScale)
                .tickFormat((d) => (Number.isInteger(d) ? d : ""))
                .tickValues(d3.range(0, d3.max(data, (d) => d.value) + 1)),
        );
    }
</script>

<div class="container">
    <svg viewBox="0 0 {width} {height}">
        <text
            x={margin.left + innerWidth / 2}
            y={margin.top / 2}
            text-anchor="middle"
            class="chart-title"
        >
            Projects per Year
        </text>
        <g
            transform="translate({margin.left}, {margin.top + innerHeight})"
            bind:this={xAxis}
        />
        <g
            transform="translate({margin.left}, {margin.top})"
            bind:this={yAxis}
        />
        <g transform="translate({margin.left}, {margin.top})">
            {#each data as d, index}
                <rect
                    x={xScale(d.label)}
                    y={yScale(d.value)}
                    width={xScale.bandwidth()}
                    height={innerHeight - yScale(d.value)}
                    fill={colorScale(d.label)}
                    opacity={selectedIndex === -1 || selectedIndex === index
                        ? 1
                        : 0.45}
                    tabindex="0"
                    role="button"
                    aria-label="{d.label}: {d.value} project{d.value === 1
                        ? ''
                        : 's'}"
                    on:click={(e) => toggleBar(index, e)}
                    on:keyup={(e) => toggleBar(index, e)}
                />
            {/each}
            {#if maxBar}
                <!-- highlight outline around the tallest bar -->
                <rect
                    x={xScale(maxBar.label)}
                    y={yScale(maxBar.value)}
                    width={xScale.bandwidth()}
                    height={innerHeight - yScale(maxBar.value)}
                    fill="none"
                    stroke="currentColor"
                    stroke-width="2"
                />
                <!-- leader line going upward from top of bar -->
                <line
                    x1={xScale(maxBar.label) + xScale.bandwidth() / 2}
                    y1={yScale(maxBar.value) - 5}
                    x2={xScale(maxBar.label) + xScale.bandwidth() / 2}
                    y2={yScale(maxBar.value) - 25}
                    stroke="currentColor"
                    stroke-width="1"
                />
                <!-- annotation text above the bar -->
                <text
                    x={xScale(maxBar.label) + xScale.bandwidth() / 2}
                    y={yScale(maxBar.value) - 30}
                    text-anchor="middle"
                    dominant-baseline="auto"
                    class="annotation"
                >
                    Most projects (tied)
                </text>
            {/if}
            <!-- x-axis label -->
            <text
                x={innerWidth / 2}
                y={innerHeight + margin.bottom - 10}
                text-anchor="middle"
                class="axis-label"
            >
                Year
            </text>
            <!-- y-axis label -->
            <text
                x={-(innerHeight / 2)}
                y={-margin.left + 30}
                text-anchor="middle"
                transform="rotate(-90)"
                class="axis-label"
            >
                Number of Projects
            </text>
        </g>
    </svg>

    <ul class="legend">
        {#each data as d}
            <li style="--color: {colorScale(d.label)}">
                <span class="swatch"></span>
                {d.label} <em>({d.value})</em>
            </li>
        {/each}
    </ul>
</div>

<style>
    svg {
        max-width: 100%;
        height: auto;
        overflow: visible;
    }

    .container {
        display: flex;
        align-items: center;
        gap: 1.5rem;
    }

    .legend {
        flex: 1;
        list-style: none;
        margin: 0;
        padding: 0;
        display: flex;
        flex-direction: column;
        gap: 0.4rem;
    }

    .legend li {
        display: flex;
        align-items: center;
        gap: 0.5rem;
    }

    .swatch {
        display: inline-block;
        width: 12px;
        height: 12px;
        border-radius: 2px;
        background-color: var(--color);
        flex-shrink: 0;
    }

    svg:hover rect:not(:hover),
    .container:focus-within rect:not(:focus-visible) {
        opacity: 50%;
    }

    rect {
        transition: 300ms;
        outline: none;
    }

    rect:focus-visible {
        stroke: white;
        stroke-width: 2px;
        stroke-dasharray: 4;
    }

    .chart-title {
        font-size: 1em;
        font-weight: bold;
        fill: currentColor;
    }

    .axis-label {
        font-size: 0.8em;
        fill: currentColor;
    }

    .annotation {
        font-size: 0.7em;
        fill: currentColor;
        font-style: italic;
    }
</style>
