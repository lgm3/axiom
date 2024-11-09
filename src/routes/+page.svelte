<script lang="ts">
  import SideBar from '../components/SideBar.svelte';
  import Spreadsheet from './Spreadsheet.svelte';
  
  let activeTab = $state(0);
</script>

<div class="app">
  <SideBar />
  <main>
    <div class="tabs">
      <button class:active={activeTab === 0} onclick={() => activeTab = 0}>
        Sheet1.csv
      </button>
      <button class:active={activeTab === 1} onclick={() => activeTab = 1}>
        Sheet2.csv
      </button>
    </div>

    <div class="content">
      {#if activeTab === 0}
        <Spreadsheet content="Sheet1.csv" />
      {:else}
        <Spreadsheet content="Sheet2.csv" />
      {/if}
    </div>
  </main>
</div>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
  }

  .app {
    display: flex;
    height: 100vh;
    color: #ffffff;
  }

  main {
    flex: 1;
    background: #1e1e1e;
    display: flex;
    flex-direction: column;
  }

  .content {
    flex: 1;
    overflow: hidden;
  }

  .tabs {
    display: flex;
    background: #252526;
    border-bottom: 1px solid #333;
  }

  .tabs button {
    padding: 8px 16px;
    background: none;
    border: none;
    color: #858585;
    cursor: pointer;
    border-right: 1px solid #333;
  }

  .tabs button.active {
    background: #1e1e1e;
    color: #ffffff;
  }
</style>
