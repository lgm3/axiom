<script lang="ts">
  export let content: string;
  
  // Generate A-Z column headers
  const columns = Array.from({ length: 26 }, (_, i) => 
    String.fromCharCode(65 + i)
  );
  
  // Generate 100 rows for demo
  const rows = Array.from({ length: 100 }, (_, i) => i + 1);
</script>

<div class="spreadsheet">
  <table>
    <thead>
      <tr>
        <th></th> <!-- Empty corner cell -->
        {#each columns as col}
          <th>{col}</th>
        {/each}
      </tr>
    </thead>
    <tbody>
      {#each rows as row}
        <tr>
          <th>{row}</th>
          {#each columns as col}
            <td contenteditable="true"></td>
          {/each}
        </tr>
      {/each}
    </tbody>
  </table>
</div>

<style>
  .spreadsheet {
    overflow: auto;
    height: 100%;
  }

  table {
    border-collapse: collapse;
    font-size: 14px;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  }

  th, td {
    border: 1px solid #444;
    min-width: 100px;
    height: 24px;
    padding: 2px 4px;
  }

  th {
    background: #1e1e1e;
    color: #888;
    font-weight: normal;
  }

  thead th {
    position: sticky;
    top: 0;
    z-index: 2;
  }

  tr th:first-child {
    position: sticky;
    left: 0;
    z-index: 1;
  }

  thead th:first-child {
    z-index: 3;
  }

  td {
    background: #252526;
    color: #fff;
  }

  td:focus {
    outline: 2px solid #007acc;
    outline-offset: -2px;
  }
</style> 