<script>
    import { base } from "$app/paths";
</script>

<svelte:head>
    <title>Assignment 2</title>
</svelte:head>

<h1>Assignment 2: Exploratory Visual Analysis</h1>

<nav>
    <ul>
        <li><a href={`${base}/`}>Home</a></li>
        <li><a href={`${base}/projects`}>Projects</a></li>
        <li><a class="current" href={`${base}/A2`}>Assignment 2</a></li>
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

<section id="questions">
    <h2>Overall Analysis Questions</h2>
    <ul>
        <li>
            Is there a correlation between class zoning and fiscal zoning?
            Motivation: One of the readings mentioned class zoning as a cause of
            social hierarchy and fiscal zoning as a cause of differences in
            economic class. From what I’ve seen and heard, I feel like there
            should be correlation between these since it would be reasonable for
            ones who make more money to have higher tax revenues.
        </li>
        <li>
            Have suburbs tried to welcome those who were excluded since the
            1970s when they wanted to preserve “status-quo”? Motivation: In my
            experience, suburbs, especially wealthy ones, still primarily exist
            of white people. How did we recover from the big downzoning?
        </li>
        <li>
            In what way does Boston’s progressive political identity conflict
            with the lived reality of segregation? Motivation: Boston is often
            seen as liberal and educated, yet it is still deeply segregated. I
            want to understand whether commitments to equity differ from
            outcomes, and why if that gap persists.
        </li>
    </ul>
</section>

<section id="results">
    <h2>Discoveries and Insights</h2>

    <figure>
        <img
            src={`${base}/images/figure 1.png`}
            alt="Greater Boston HOLC Map"
        />
        <figcaption>
            Figure 1. HOLC Categories Across Greater Boston — Red indicates
            hazardous “D” grade areas, while green indicates “A” graded
            neighborhoods.
        </figcaption>
        <p>
            First, I looked at the HOLC Neighborhood Grade for Greater Boston
            and the cities around it. The HOLC’s rating of a neighborhood as a
            real-estate/mortgage lending investment risk. They look at things
            like age/condition of housing, proximity to amenities, economic
            status of residents, racial/ethnic composition, so the grades act as
            a creditworthiness score for lending. The scores are only given to
            residential areas, so I grayed out Business and Industrial,
            Commercial, and Industrial. Residential areas are given either a
            Best, Still Desirable, Definitely Declining, or Hazardous. It seems
            that the Hazardous areas are concentrated near the middle, with
            cities like Boston, Cambridge, Everett, Chelsea, Revere, and Malden.
            The Best and Still Desirable ones concentrated near the outer
            portions of the graph. This seems to fit what I assumed, which was
            that wealthy suburbs usually have higher concentrations of white
            people, which is a metric they used to assign the category.
        </p>
    </figure>

    <figure>
        <img
            src={`${base}/images/figure 2.png`}
            alt="Number of Areas in HOLC City Survey Programs"
        />
        <figcaption>
            Figure 2. This map shows the number of surveyed areas across various
            Greater Boston cities, with bigger circles indicating more.
        </figcaption>
        <p>
            The cities were further divided up into areas, and each area was
            assigned a number as an ID. I wanted to see how many areas they
            surveyed for each city because it gives insight into much attention
            and geographic detail the HOLC survey devoted to different
            municipalities. Cities with more surveyed areas were mapped in finer
            resolution, which can reflect their size, housing density, and
            perceived importance to lending and development. Also, if a city has
            a lot of surveyed areas, the map breaks it into many smaller pieces,
            meaning the surveyors were capturing more
            neighborhood-to-neighborhood variation there, instead of treating
            the city as just a few big zones. It could also show where the HOLC
            concentrated its mapping effort. More surveyed areas often means
            more granular categorization of neighborhoods, which matters because
            finer-grained mapping can shape where credit is steered or withheld
            and how sharply boundaries of “risk” are drawn. It seems like there
            were the most surveyed areas in Boston, which makes sense because
            Boston is the biggest city in terms of area on this map.
        </p>
    </figure>

    <figure>
        <img
            src={`${base}/images/figure 3.png`}
            alt="Grades for Areas of Boston Cities"
        />
        <figcaption>
            Figure 3. Grades for Areas of Boston Cities. This visualization
            shows the breakdown of A, B, C, and D zones in Greater Boston's
            neighborhoods.
        </figcaption>
        <p>
            I dove deeper into each area of every city and found their
            corresponding grades. The grades align with the categories shown in
            the first figure: A (Best), B (Still Desirable), C (Definitely
            Declining), and D (Hazardous). As I mentioned earlier, only
            residential areas were graded, so I excluded industrial and
            commercial areas since they were not assigned a grade. This
            visualization corroborates with the previous two, as it not only
            shows the breakdown of how many areas were surveyed in each city but
            also reveals the specific grade assigned to those areas. By focusing
            solely on residential zones, this map highlights the spatial
            segregation and inequality that may have been further exacerbated by
            the grading system.
        </p>
    </figure>

    <figure>
        <img
            src={`${base}/images/figure 4.png`}
            alt="Cities with Best and Worst HOLC Grades"
        />
        <figcaption>
            Figure 4. Cities with Best and Worst HOLC Grades. Bar chart of all
            the cities, with only the number of areas with A and D grades.
        </figcaption>
        <p>
            While the dataset does not contain explicit fiscal zoning data such
            as tax revenue or municipal budgets, the grades assigned to
            residential areas by the HOLC provide valuable insight into the
            relationship between class zoning and fiscal zoning. In this
            visualization, I focused on cities with areas graded A (Best) and D
            (Hazardous). The A areas, typically associated with wealthier
            populations, higher property values, and greater financial
            stability, likely generate higher municipal tax revenues due to
            their affluence. In contrast, the D zones, often found in
            economically disadvantaged areas, correspond to lower property
            values and reduced tax revenue potential. From the <a
                href="https://dsl.richmond.edu/panorama/redlining/map/MA/Boston/context#loc=11/42.3351/-71.1643"
                >source</a
            >
            of the dataset, I looked at the estimated annual family income. For example,
            for a city like Milton which has an estimated annual family income of
            $3,000-$7,500 while an area with D grade in Boston has an estimated annual
            family income of $500-$1,500. The difference in estimated annual family
            income between the A and D grade areas are quite prevalent and drastic.
        </p>
        <p>
            By comparing these two grades across different municipalities, the
            chart highlights how higher-grade zones are typically linked to
            wealthier communities, while lower-grade zones correlate with areas
            facing economic decline and fewer fiscal resources. This reinforces
            the idea that class zoning (through the HOLC grades) directly
            influences fiscal zoning by shaping the tax base and economic
            capacity of different neighborhoods. By correlating the distribution
            of residential areas with economic indicators, we can infer that
            there is a strong relationship between class zoning (HOLC grades)
            and fiscal zoning. For example, areas that were rated A (Best) were
            likely to attract wealthier residents, who would pay higher property
            taxes, thereby contributing to higher municipal revenues.
            Conversely, C/D zones often correspond to lower-income populations,
            where tax revenues are typically lower due to reduced property
            values.
        </p>
    </figure>

    <figure>
        <img
            src={`${base}/images/figure 5.png`}
            alt="Areas and Their Corresponding Grades"
        />
        <figcaption>
            Figure 5. Areas and Their Corresponding Grades. Within each city,
            every area is color coded by the grade received.
        </figcaption>
        <p>
            The grid visualization displays the breakdown of A/B vs C/D grades
            for each city. By coloring the areas based on their HOLC grade, we
            can visually compare wealthier areas (A/B grades) to poorer areas
            (C/D grades). For example, cities like Arlington and Belmont have a
            higher concentration of A/B zones, indicating that these areas are
            historically more affluent and likely had higher property values,
            aligning with the wealthier, desirable residents. In contrast, areas
            like Lynn, Malden, and Quincy feature more C/D zones, which
            historically housed lower-income populations, as shown in the red
            and orange colors. This stark difference underscores the legacy of
            class zoning and its lasting impact on suburban development and
            racial integration.
        </p>
        <p>
            Although our current dataset doesn’t include time series data, I
            investigated the inhabitants that made up the areas in the HOLC map.
            This information, though not in the dataset itself, is part of the
            <a
                href="https://dsl.richmond.edu/panorama/redlining/map/MA/Boston/areas#mapview=full&loc=12/42.3138/-71.0811"
                >original source</a
            >
            and provides insight into the social composition of the areas. Looking
            at areas graded A and B (Best and Still Desirable), these neighborhoods
            typically attracted higher-income residents or those deemed “desirable”
            or “high class” by the HOLC surveyors. In contrast, areas graded C and
            D (Definitely Declining and Hazardous) were home to lower-income, racially
            marginalized groups, including Black, immigrant, and Jewish populations.
            They were deemed as “foreign” or “lower class”. This historical classification
            highlights the racial and economic segregation embedded in the zoning
            practices of the time.
        </p>
        <p>
            While Greater Boston has seen a significant increase in racial
            diversity since the 1970s, the pace of change has not been
            consistent across all suburbs. The Black population in Greater
            Boston more than doubled from 1980 to 2020, with many of these new
            residents settling in the suburbs that were once predominantly
            white. However, while there has been progress, suburbs that were
            previously racially homogeneous have often been resistant to full
            integration due to zoning laws and economic barriers. These changes
            in racial composition reflect shifts in housing availability, with
            immigration and affordable housing policies playing significant
            roles in opening suburban areas to a more diverse population. (<a
                href="https://commonwealthbeacon.org/economy/greater-bostons-black-population-becoming-more-diverse-dispersed/?"
                >Commonwealth Boston</a
            >,
            <a
                href="https://www.wbur.org/news/2023/04/06/greater-boston-black-population-is-growth-diversity-report?"
                >WBUR</a
            >)
        </p>
    </figure>

    <figure>
        <img
            src={`${base}/images/figure 6.png`}
            alt="Grades for Areas of Boston Cities (Liberal vs Evenly Split)"
        />
        <figcaption>
            Figure 6. Grades for Areas of Boston Cities (Liberal vs Evenly
            Split). First 4 cities are liberal leanining, the rest are split.
        </figcaption>
        <p>
            Using the HOLC grade visualization, we can see a clear connection
            between the political identity of various cities and the
            distribution of A/B and C/D zones. Cities like Boston, Chelsea,
            Revere, and Winthrop, which are generally seen as liberal, have a
            significant number of C/D zones (indicating economic decline and
            lower investment), even though these cities are known for their
            progressive political stances. Despite their liberal policies, the
            legacy of segregation is still visible in these areas, with
            marginalized communities often clustered in C/D zones. On the other
            hand, cities like Brookline, Dedham, Milton, Needham, Quincy, and
            Saugus, which are more evenly split politically, show a more mixed
            distribution of A/B vs C/D zones. These cities do not lean heavily
            in one direction politically, and their zoning patterns reflect a
            balance between wealthier areas (A/B zones) and areas of economic
            decline (C/D zones). However, even in these more politically mixed
            cities, the presence of C/D zones shows that historical zoning
            practices still play a significant role in determining the economic
            and racial segregation of neighborhoods. I got the information about
            politics from this <a
                href="https://bestneighborhood.org/conservative-vs-liberal-map-boston-ma/"
                >source</a
            >.
        </p>
        <p>
            The visualization reinforces the idea that progressive political
            identity does not automatically result in integrated communities.
            Despite liberal policies in Boston and Chelsea, segregation persists
            due to factors like zoning laws, housing policies, and residential
            discrimination, creating a disconnect between the city's political
            commitment to equity and the actual lived experience of its
            residents.
        </p>
    </figure>
</section>

<section id="summary">
    <h2>Summary & Conclusion</h2>
    <p>
        Through this analysis, it became clear that historical class zoning, as
        reflected in the HOLC grades, continues to have a lasting impact on
        economic and racial segregation in the Greater Boston area. The A/B
        (Best and Still Desirable) zones historically attracted wealthier,
        predominantly white populations, while C/D (Definitely Declining and
        Hazardous) areas were often home to lower-income and marginalized
        communities, including Black, immigrant, and Jewish populations. This
        division in zoning practices reinforced economic and racial hierarchies,
        influencing property values and tax revenues in different neighborhoods.
    </p>
    <p>
        The visualization of HOLC grades further highlighted the persistence of
        segregation in liberal cities like Boston and Chelsea, where significant
        portions of the population live in C/D zones despite the progressive
        political identity of these areas. These cities, while advocating for
        equity and inclusion, still exhibit clear divisions in wealth and
        opportunity that are rooted in their historical zoning practices. In
        contrast, more evenly split political cities, such as Brookline and
        Saugus, show a more mixed distribution of A/B vs C/D zones, suggesting
        that political identity may not always be directly aligned with racial
        and economic integration.
    </p>
    <p>
        Additionally, while Greater Boston has seen an increase in racial
        diversity since the 1970s, particularly in suburban areas, the pace of
        this integration has been slow and uneven. Factors such as housing
        policies, zoning laws, and economic barriers have continued to limit the
        full integration of previously excluded populations into suburban
        communities. Despite some progress, the legacy of segregation remains a
        deep-rooted challenge in the region, demonstrating that commitments to
        equity at the political level do not always lead to immediate, tangible
        outcomes for marginalized communities.
    </p>
    <p>
        In conclusion, the analysis of HOLC grades and the distribution of
        wealth and racial composition in Greater Boston provides a strong visual
        and statistical case for the lasting effects of class zoning. It also
        highlights the disconnect between progressive political identities and
        the economic disparities that continue to shape Boston’s neighborhoods.
    </p>
</section>
