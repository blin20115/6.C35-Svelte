<script>
  import { base } from "$app/paths";
</script>

<svelte:head>
  <title>Resume</title>
</svelte:head>

<h1>Resume</h1>

<h4>
  <a
    href="https://drive.google.com/file/d/1qnaWYsIOCNXOS29om2rZQBUuWrLEVJ5J/view?usp=sharing"
    >Link to Full Resume</a
  >
</h4>

<section>
  <h3>Education</h3>

  <article>
    <h4>Massachusetts Institute of Technology</h4>
    <p>Cambridge, MA</p>
    <p>Sep 2024 - Present</p>

    <ul>
      <li>Bachelor's of Science in Computer Science and Mathematics</li>
      <li>
        Relevant Coursework: Fundamentals of Programming, Introduction to
        Algorithms, Probability and Random Variables, Introduction to Machine
        Learning, Fundamentals of Statistics,
      </li>
    </ul>
  </article>
</section>

<section>
  <h3>Experience</h3>

  <article>
    <h4>Software Developement Enginnering Intern @ Amazon Web Services</h4>
    <p>Seattle, WA</p>
    <p>May 2025 - Aug 2025</p>
    <ul>
      <li>
        Integrated 5 APIs to enable customers to query logs directly via AWS CLI
        commands
      </li>
      <li>
        Designed DynamoDB implementation for metadata mapping, improving lookup
        speed and enhancing user experience
      </li>
      <li>
        Created comprehensive end-to-end test cases, ensuring reliable and
        accurate request handling across various edge cases through 90%+ code
        coverage
      </li>
    </ul>
  </article>

  <article>
    <h4>Undergraduate Student Researcher @ MIT Department of Physics</h4>
    <p>Cambridge, MA</p>
    <p>Oct 2024 - Jan 2025</p>
    <ul>
      <li>
        Contributed to the Nuclear Weapons Education Project, supporting public
        education on nuclear policy and science
      </li>
      <li>
        Developed an interactive web simulation using HTML, CSS, and JavaScript
        to model the effects of nuclear weapons
      </li>
    </ul>
  </article>
</section>
