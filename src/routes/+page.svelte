<script lang="ts">
  const ROWS = 10;
  const COLS = 6;

  // Initialize grid with empty strings
  let grid = $state(
    Array(ROWS).fill(null).map(() => 
      Array(COLS).fill("")
    )
  );

  // Convert column number to letter (0 = A, 1 = B, etc.)
  function getColumnLabel(col: number): string {
    return String.fromCharCode(65 + col);
  }
</script>

<main>
  <div class="spreadsheet">
    <!-- Header row -->
    <div class="header-row">
      <div class="corner-cell"></div>
      {#each Array(COLS) as _, col}
        <div class="header-cell">{getColumnLabel(col)}</div>
      {/each}
    </div>

    <!-- Data rows -->
    {#each grid as row, rowIndex}
      <div class="row">
        <div class="row-header">{rowIndex + 1}</div>
        {#each row as cell, colIndex}
          <input
            class="cell"
            type="text"
            bind:value={grid[rowIndex][colIndex]}
          />
        {/each}
      </div>
    {/each}
  </div>
</main>

<style>
  .spreadsheet {
    font-family: Arial, sans-serif;
    border: 1px solid #ccc;
    display: inline-block;
  }

  .header-row {
    display: flex;
    background-color: #f3f3f3;
  }

  .corner-cell {
    width: 50px;
    border-right: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
  }

  .header-cell {
    width: 100px;
    text-align: center;
    padding: 4px;
    border-right: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
    font-weight: bold;
  }

  .row {
    display: flex;
  }

  .row-header {
    width: 50px;
    text-align: center;
    padding: 4px;
    background-color: #f3f3f3;
    border-right: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
    font-weight: bold;
  }

  .cell {
    width: 100px;
    padding: 4px;
    border: none;
    border-right: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
  }

  .cell:focus {
    outline: 2px solid #0066cc;
    outline-offset: -2px;
  }
</style>
