<script>
  import { base } from "$app/paths";
</script>

<svelte:head>
  <title>Contact me</title>
</svelte:head>

<h1>Contact</h1>

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
