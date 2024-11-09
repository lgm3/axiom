<script lang="ts">
  import Spreadsheet from './Spreadsheet.svelte';
  let activeTab = $state(0);
</script>

<main>
  <div class="tabs">
    <button 
      class:active={activeTab === 0} 
      onclick={() => activeTab = 0}
    >
      Sheet1.csv
    </button>
    <button 
      class:active={activeTab === 1} 
      onclick={() => activeTab = 1}
    >
      Sheet2.csv
    </button>
  </div>

  <div class="content">
    {#if activeTab === 0}
      <Spreadsheet content="Spreadsheet 1 Content" />
    {:else}
      <Spreadsheet content="Spreadsheet 2 Content" />
    {/if}
  </div>
</main>

<style>
  main {
    height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .tabs {
    background: #1e1e1e;
    border-bottom: 1px solid #333;
  }

  button {
    padding: 8px 16px;
    border: none;
    background: transparent;
    color: #969696;
    cursor: pointer;
  }

  button.active {
    background: #252526;
    color: white;
    border-bottom: 2px solid #007acc;
  }

  .content {
    flex: 1;
    background: #252526;
  }

  .spreadsheet {
    padding: 20px;
    color: white;
  }
</style>
