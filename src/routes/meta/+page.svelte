<script>
    import { base } from "$app/paths";
    import { onMount } from "svelte";
    import * as d3 from "d3";
    import BarHorizontal from "$lib/BarHorizontal.svelte";

    let width = 1000,
        height = 600;
    let margin = { top: 10, right: 10, bottom: 30, left: 20 };
    let usableArea = {
        top: margin.top,
        right: width - margin.right,
        bottom: height - margin.bottom,
        left: margin.left,
    };
    usableArea.width = usableArea.right - usableArea.left;
    usableArea.height = usableArea.bottom - usableArea.top;

    let locData = [];
    let commits = [];
    let barData = [];

    let xAxis, yAxis, yAxisGridlines;

    onMount(async () => {
        locData = await d3.csv(`${base}/loc.csv`, (row) => ({
            ...row,
            line: Number(row.line),
            length: Number(row.length),
            depth: Number(row.depth),
            date: new Date(row.date + "T00:00" + row.timezone),
            datetime: new Date(row.datetime),
        }));

        commits = d3
            .groups(locData, (d) => d.commit)
            .map(([commit, lines]) => {
                let first = lines[0];
                let { author, date, time, timezone, datetime } = first;
                return {
                    id: commit,
                    url:
                        "https://github.com/vis-society/lab-7/commit/" + commit,
                    author,
                    date,
                    time,
                    timezone,
                    datetime,
                    hourFrac: datetime.getHours() + datetime.getMinutes() / 60,
                    totalLines: lines.length,
                    lines: lines,
                };
            });

        commits = d3.sort(commits, (d) => -d.totalLines);

        barData = d3
            .rollups(
                locData,
                (v) => v.length,
                (d) => d.type,
            )
            .sort((a, b) => b[1] - a[1])
            .map(([language, lines]) => ({ label: language, value: lines }));
    });

    $: [minDate, maxDate] = d3.extent(commits.map((d) => d.date));
    $: maxDatePlusOne = new Date(maxDate);
    $: maxDatePlusOne.setDate(maxDatePlusOne.getDate() + 1);

    $: xScale = d3
        .scaleTime()
        .domain([minDate, maxDatePlusOne])
        .range([usableArea.left, usableArea.right])
        .nice();

    $: yScale = d3
        .scaleLinear()
        .domain([24, 0])
        .range([usableArea.bottom, usableArea.top]);

    $: rScale = d3
        .scaleSqrt()
        .domain(d3.extent(commits, (d) => d.totalLines))
        .range([5, 30]);

    $: {
        d3.select(xAxis).call(d3.axisBottom(xScale));
        d3.select(yAxis).call(
            d3
                .axisLeft(yScale)
                .tickFormat((d) => String(d % 24).padStart(2, "0") + ":00"),
        );
        d3.select(yAxisGridlines).call(
            d3.axisLeft(yScale).tickFormat("").tickSize(-usableArea.width),
        );
    }
</script>

<svelte:head>
    <title>Meta</title>
</svelte:head>

<h1>Meta</h1>
<p>Stats about the codebase behind this site.</p>

<h3>Commits by time of day</h3>
<svg viewBox="0 0 {width} {height}">
    <g
        class="gridlines"
        transform="translate({usableArea.left}, 0)"
        bind:this={yAxisGridlines}
    />
    <g transform="translate(0, {usableArea.bottom})" bind:this={xAxis} />
    <g transform="translate({usableArea.left}, 0)" bind:this={yAxis} />
    <g class="dots">
        {#each commits as commit, index}
            <circle
                cx={xScale(commit.datetime)}
                cy={yScale(commit.hourFrac)}
                r={rScale(commit.totalLines)}
                fill="steelblue"
                fill-opacity="0.5"
            />
        {/each}
    </g>
</svg>

<BarHorizontal data={barData} />

<style>
    svg {
        overflow: visible;
    }

    .gridlines {
        stroke-opacity: 0.2;
    }
</style>
