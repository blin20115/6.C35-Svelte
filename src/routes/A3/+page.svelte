<script>
    import { base } from "$app/paths";
</script>

<svelte:head>
    <title>Assignment 3: Visualization Critique & Redesign</title>
</svelte:head>

<h1>Assignment 3: Visualization Critique & Redesign</h1>

<section id="spiral_img">
    <figure>
        <img
            src={`${base}/images/cov19_spiral.png`}
            alt="New Covid-19 Cases in the US from 2020-2022"
            width="600"
            height="650"
        />
        <figcaption>
            At the peak of the Omicron variant of the COVID-19 pandemic, the New
            York Times published an
            <a
                href="https://www.nytimes.com/2022/01/06/opinion/omicron-covid-us.html?unlocked_article_code=1.zk4.stTQ.3bTjWtsFU-ls&smid=url-share"
                >opinion article</a
            > by Dr. Jeffrey Shaman, an infectious disease modeler and epidemiologist
            at Columbia University whose team built one of the first models of COVID-19.
            The article lead with the following, widely-discussed data visualization
            (above).
        </figcaption>
    </figure>
</section>

<section id="insights">
    <h2>Insights</h2>
    <ul>
        <li>
            There's a clear seasonal rhythm, since winters are consistently the
            worst, summers relatively calmer. The spiral format actually makes
            this quite intuitive since the same months stack on top of each
            other across years.
        </li>
        <li>
            Summer 2020 (the bottom of the innermost loop, around July) is
            almost paper-thin, since cases were relatively low early in the
            pandemic
        </li>
        <li>
            Cases started in March 2020, since that's the start of the red line,
            but didn't have visible width until April.
        </li>
    </ul>
</section>

<section id="critique">
    <h2>Critique</h2>
    <p>
        Its greatest strength is the seasonal stacking. By looping each year
        around the same calendar positions, it makes the recurring winter surges
        immediately intuitive without requiring the reader to explicitly compare
        across years. The dramatic spike bursting off the top of the chart is
        also powerful. It communicates the sheer scale of that wave in a way a
        standard line chart might not, and feels appropriate for an opinion
        piece trying to convey urgency rather than precision. The minimalist
        labeling (just a few month anchors, year markers, and a single legend
        item) keeps the design uncluttered, and the muted pink palette is easy
        on the eye while still conveying something alarming.
    </p>

    <p>
        However, the design has some meaningful readability costs. The width
        encoding for case counts is harder to decode than a standard
        position-on-axis encoding. The 150K legend marker is hard to follow, and
        thin bands (representing lower but still significant case counts) are
        nearly impossible to quantify, making it difficult to compare. The 7-day
        average line is labeled but never explained, which may leave general
        readers, the likely audience for an NYT opinion piece, unsure what it
        means or why it differs from the shaded band. The spiral structure also
        demands a degree of visual literacy, since readers must consciously
        trace the path to orient themselves by year and month, and there's no
        clear visual entry point guiding where to start reading.
    </p>
</section>

<section id="sketches">
    <h2>Visualization Sketches</h2>

    <h3>Figure 1</h3>
    <figure>
        <img
            src={`${base}/images/a3-line-chart.jpg`}
            alt="Line chart of new COVID cases in US from 2020-2022"
            width="500"
            height="350"
        />
        <figcaption>
            Replaced the spiral with a standard time-series line chart, x-axis
            as dates (Mar 2020 – Jan 2022), y-axis as 7-day average of new cases
            (says daily in the chart but that's not right). Key peaks are
            annotated directly on the chart.
        </figcaption>

        <ul>
            <li>
                Motivation: Fix the core readability problem. Position on a
                shared y-axis is far easier to decode than band width.
            </li>
            <li>
                Key decisions: Direct annotations name each surge so readers
                don't need prior knowledge.
            </li>
            <li>
                What works: Omicron's scale is still dramatic; values are
                actually readable; the 7-day average line now makes intuitive
                sense.
            </li>
            <li>
                What's lost: The seasonal stacking across years that made the
                spiral smart. A reader has to mentally compare winters
                themselves.
            </li>
            <li>
                Next: Can we preserve year-over-year seasonal comparison more
                explicitly?
            </li>
        </ul>
    </figure>

    <h3>Figure 2</h3>
    <figure>
        <img
            src={`${base}/images/a3-bar.jpg`}
            alt="Bars depicting new COVID-19 cases, separated by year"
            width="500"
        />
        <figcaption>
            Three side-by-side circular charts, one per year (2020, 2021, 2022),
            each arranged like a clock with months on the outside and bar height
            radiating outward representing case counts. Same scale across all
            three so they're directly comparable.
        </figcaption>
    </figure>

    <ul>
        <li>
            Motivation: Keep the seasonal/circular intuition from the original
            while eliminating the confusion that comes with having to figure out
            which loop we are looking at
        </li>
        <li>
            Key decisions: Three separate polar charts, one per year, on the
            same scale, so Omicron's 2022 chart is visibly more "filled in."
            Month labels sit on the outside like a clock.
        </li>
        <li>
            What works: Year-over-year comparison is immediate, no spiral
            tracing required, and winter clustering is obvious.
        </li>
        <li>
            What's lost: Continuous time flow is broken, for example between
            winter 2020 to early 2021.
        </li>
        <li>
            Next: What if we kept it grid-based but made it even more intuitive
            for reading?
        </li>
    </ul>

    <h3>Figure 3</h3>
    <figure>
        <img
            src={`${base}/images/a3-heatmap.jpg`}
            alt="Heatmap of COVID-19 cases in US"
            width="300"
        />
        <figcaption>
            A grid where each row is a month (Jan–Dec) and each column is a year
            (2020, 2021, 2022), with color intensity encoding average daily
            cases that month.
        </figcaption>
        <ul>
            <li>
                Motivation: Address the "compare same season across years"
                problem directly, since we can read across a row to compare all
                Januaries at once.
            </li>
            <li>
                Key decisions: Color intensity encodes magnitude (easier for
                general audiences than width).
            </li>
            <li>
                What works: Seasonal patterns are scannable row-by-row, winter
                waves are obvious, Jan 2022 stands out dramatically in color.
            </li>
            <li>What's lost: Continuous time flow within months is hidden.</li>
            <li>
                Tradeoff: Precision and clarity over emotional impact, which may
                be more appropriate for a news article than an opinion piece
                trying to alarm.
            </li>
        </ul>
    </figure>
</section>

<section id="final">
    <h2>Final Visualization Design</h2>
    <img
        src={`${base}/images/a3-final.png`}
        alt="Final graph for COVID cases in US"
        width="500"
    />
</section>

<section id="writeup">
    <h2>Final Writeup</h2>

    <p>
        The goal of this visualization is to communicate how the severity of
        COVID-19 surges escalated dramatically over time in the United States,
        culminating in the Omicron wave of early 2022 which dwarfed every prior
        peak. To tell this story clearly, I chose an area chart with the date on
        the x-axis and average daily new confirmed cases on the y-axis,
        aggregated to the monthly level. Monthly aggregation was a deliberate
        choice, since it smooths out the noise of day-to-day reporting
        inconsistencies while still preserving the shape and timing of each
        major surge. The chart is faceted by year into three panels, which
        serves two purposes. It eliminates the visual clutter of a single
        continuous timeline and allows the reader to compare the same seasons
        across years at a glance. A consistent pink-to-red color family was
        chosen intentionally to evoke both alarm and a sense of escalation, with
        2020 rendered in a cooler blue to signal the "before" era and 2021–2022
        in increasingly saturated reds. Direct annotations on each peak label
        the surge by name and provide the exact average daily case count, so
        readers can quantify the comparison without needing to read off the
        y-axis themselves. One tradeoff of this design is that monthly
        aggregation obscures within-month variation — for instance, the Omicron
        spike was even more extreme at its single-day peak than the monthly
        average suggests, meaning the chart actually understates how sharp that
        surge was.
    </p>

    <p>
        This redesign directly addresses several of the critiques I raised about
        the original spiral visualization. The biggest issue, that band width is
        a hard encoding to decode compared to just reading a y-axis, is fixed
        here since readers can now actually see and compare the peak values
        across surges. The jargon-y "7-day average" label is gone, replaced with
        plain language, and the direct annotations mean you don't need to
        already know when Delta or Omicron happened to understand the chart.
        However, there were tradeoffs. The thing the spiral actually did really
        well, with stacking the same months across years so you could
        immediately see that winters were always the worst, is somewhat lost in
        the panel layout, since you have to consciously look across three
        separate charts to notice that pattern rather than it just hitting you
        visually. Making the chart easier to read precisely meant giving up some
        of the "aha" moment that the spiral delivered. So while I think this
        design is cleaner and more honest than the original, it's a tradeoff.
    </p>
</section>
