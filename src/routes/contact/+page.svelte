<svelte:head>
  <title>Contact me</title>
</svelte:head>

<h1>Contact</h1>

<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="projects">Projects</a></li>
    <li><a href="A2">Assignment 2</a></li>
    <li><a class="current" href=".">Contact</a></li>
    <li><a href="resume">Resume</a></li>
    <li><a href="https://github.com/blin20115" target="_blank">GitHub</a></li>
  </ul>
</nav>

<form action="mailto:blin15@mit.edu" method="GET">
  <label>
    Email:
    <input name="email" type="email" />
  </label>

  <label>
    Subject:
    <input name="subject" />
  </label>

  <label>
    Message:
    <textarea name="body"></textarea>
  </label>

  <button>Send</button>
</form>
