<script>
    import { base } from "$app/paths";
</script>

<svelte:head>
    <title>Assignment 4: Persuasive or Deceptive Visualization?</title>
</svelte:head>

<h1>Assignment 4: Persuasive or Deceptive Visualization?</h1>

<section id="proposition">
    <h2>
        Proposition: States that restrict abortion clinic access don't reduce
        abortions, but instead they redirect them, pushing residents to cross
        state lines while turning neighboring states into regional hubs.
    </h2>
</section>

<section id="for">
    <h2>FOR the Proposition</h2>
    <figure>
        <img
            src={`${base}/images/a4-for.png`}
            alt="Restrictions don't stop abortions -- they export them"
        />
        <figcaption>
            States with the highest abortion restrictions see the greatest share
            of residents traveling out of state for care: Missouri (99%),
            Wyoming (88%), and South Dakota (84%), while states with fewer
            restrictions and more clinics perform abortions at higher rates,
            suggesting restrictions displace rather than reduce abortions.
        </figcaption>
    </figure>

    <h3>Design Decisions and Rationale:</h3>
    <ul>
        <li>
            <strong
                >Annotating Missouri, Wyoming, and South Dakota with exact
                travel percentages (Score: +1.5).</strong
            >
            Calling out the three most extreme states by name with precise numbers
            (99%, 88%, 84%) makes the pattern feel concrete and data-driven. It directs
            the reader's eye to the strongest evidence for the proposition. The main
            earnestness caveat is that these three are outliers, and labeling only
            them implicitly suggests they're representative of a broader pattern
            when most states cluster much lower.
        </li>
        <li>
            <strong
                >Red color scale for out-of-state travel (Score: -0.5).</strong
            >
            Red carries connotations of danger or alarm, priming readers to interpret
            high out-of-state travel as a problem before they've formed their own
            judgment. A neutral sequential scale (e.g. light to dark blue) would
            be more objective. This was a deliberate choice to trigger an emotional
            response aligned with the proposition.
        </li>
        <li>
            <strong>Dual encoding: fill color + circle size (Score: +1).</strong
            >
            Using two encodings simultaneously, state color for displacement, circle
            size for abortions performed, lets readers see both sides of the story
            on one map. States that are light-colored (low travel) with large circles
            visually read as "destination states," which directly supports the displacement
            narrative. It's an earnest choice in that both variables are faithfully
            represented, though the combination steers interpretation.
        </li>
        <li>
            <strong
                >Title framing: "Restrictions Don't Stop Abortions — They Export
                Them" (Score: -1).</strong
            >
            The title asserts the proposition's conclusion as established fact rather
            than a hypothesis the visualization is exploring. This is one of the
            most persuasive elements because readers often absorb titles uncritically.
            An earnest alternative would be something descriptive like "Out-of-State
            Abortion Travel by State, 2020." The assertive framing was a deliberate
            tradeoff between persuasiveness and neutrality.
        </li>
        <li>
            <strong
                >Underlying policy context from Guttmacher's interactive policy
                map (Score: +2)</strong
            >
            Cross-referencing the visualization against Guttmacher's
            <a href="https://states.guttmacher.org/policies/"
                >state policy tracker</a
            > confirms that Missouri, Wyoming, and South Dakota are among the most
            restrictive states in the country, validating that the out-of-state travel
            pattern aligns with policy restrictiveness rather than being coincidental.
            This is a fully earnest decision, grounding the visual pattern in an
            independent policy dataset strengthens the causal argument and is transparently
            verifiable by any reader.
        </li>
    </ul>
</section>

<section id="against">
    <h2>AGAINST the Proposition</h2>
    <figure>
        <img
            src={`${base}/images/a4-against.png`}
            alt="Abortion rates are climbing across the country"
        />
        <figcaption>
            Abortion rates increased in the majority of states between 2017 and
            2020, including in Oklahoma (+100%), Mississippi (+42%), and
            Kentucky (+26%), all classified as very restrictive states by the
            Guttmacher Institute, suggesting that restrictions alone do not
            suppress abortion rates. Missouri (-98%) and South Dakota (-74%)
            excluded as statistical outliers.
        </figcaption>

        <h3>Design Decisions and Rationale:</h3>
        <ul>
            <li>
                <strong
                    >Annotating Oklahoma, Mississippi, and Kentucky as "very
                    restrictive states" (Score: +1.5).</strong
                >
                Grounding the three highest-increase states in their actual policy
                classification from the Guttmacher Institute is a transparent, verifiable
                claim that strengthens the against argument considerably. It preempts
                the reader's assumption that rising rates only occur in permissive
                states. The mild deception is that these states' increases may partly
                reflect in-migration from neighboring states.
            </li>
            <li>
                <strong
                    >Excluding Missouri (-98%) and South Dakota (-74%) as
                    "statistical outliers" (Score: -1.5).</strong
                >
                These two states are the strongest evidence for the proposition and
                their exclusion is the most deceptive decision in this visualization.
                Labeling them as statistical outliers in the caption gives the exclusion
                a methodological veneer, but there's no principled statistical reason
                to exclude them. Keeping them would dramatically change the visual
                impression of the chart.
            </li>
            <li>
                <strong>Truncated x-axis (-30 to 100) (Score: -1).</strong>
                The axis range is set to start at -30 rather than the true minimum
                of -98, which compresses the negative bars and makes the declining
                states look like minor exceptions. A reader paying close attention
                would notice West Virginia's bar doesn't extend to its true value,
                but most readers won't catch it. This is a deceptive technique that
                changes the visual balance of the chart without technically misrepresenting
                any individual value.
            </li>
            <li>
                <strong
                    >Diverging color scale centered at zero (Score: +1).</strong
                >
                Using blue for increases and orange for decreases is a straightforward,
                readable encoding that helps readers immediately distinguish rising
                from falling states. Centering at zero is technically earnest. However
                the choice of blue (neutral/cool) for increases and orange (warning)
                for decreases subtly frames rising rates as normal and declining
                rates as anomalous, which aligns with the against narrative.
            </li>
            <li>
                <strong
                    >Title framing: "Abortion Rates Are Climbing Across Much of
                    the Country" (Score: -1).</strong
                >
                Like the first visualization, the title asserts a conclusion rather
                than describing the data. "Much of the country" is vague enough to
                be technically defensible, since more states did see increases than
                decreases in this filtered view, but it obscures that the most dramatic
                changes were declines, and that the two biggest declines were quietly
                removed from the chart.
            </li>
        </ul>
    </figure>
</section>

<section id="reflection">
    <h2>Final Reflection</h2>
    <p>
        Going into this assignment I assumed the "deceptive" visualization would
        feel obviously wrong to make, but it actually didn't, and that was the
        surprising part. Most of the choices that made Visualization 2
        misleading were things I could easily rationalize: excluding Missouri
        because it's extreme, truncating the axis because the chart "looks
        cleaner," framing the title assertively because that's just good
        communication. None of it felt like lying in the moment, which made me
        realize how easy it is to deceive an audience while convincing yourself
        you're being reasonable.
    </p>
    <p>
        The hardest part was drawing a line between persuasion and manipulation.
        Both visualizations make argumentative choices, like the red color scale
        in Visualization 1, the annotation calling out restrictive states in
        Visualization 2, but some feel more defensible than others. I think the
        closest thing to a workable definition of ethical visualization is
        whether you'd be comfortable explaining every decision out loud to a
        skeptical reader. The Missouri exclusion in Visualization 2 doesn't pass
        that test, and I'd have to admit I removed it because it hurt my
        argument, not because it was genuinely an outlier. That feels like the
        real boundary, not whether a choice is technically accurate, but whether
        your reasoning for it holds up under scrutiny.
    </p>
</section>
