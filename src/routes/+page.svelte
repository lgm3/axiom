<script lang="ts">
  import { invoke } from "@tauri-apps/api/core";

  let name = $state("");
  let greetMsg = $state("");

  async function greet(event: Event) {
    event.preventDefault();
    greetMsg = await invoke("greet", { name });
  }
</script>

<main>
  <form onsubmit={greet}>
    <input placeholder="Enter a name..." bind:value={name} />
    <button type="submit">Greet</button>
  </form>
  <p>{greetMsg}</p>
</main>

<style>
  main {
    padding: 1em;
    text-align: center;
  }

  input, button {
    padding: 0.5em;
    margin: 0.5em;
  }
</style>
