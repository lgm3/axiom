<script lang="ts">
  type ActivityItem = {
    id: string;
    icon: string;
    label: string;
  };

  const activities: ActivityItem[] = [
    { id: 'explorer', icon: '📁', label: 'Explorer' },
    { id: 'search', icon: '🔍', label: 'Search' },
    { id: 'git', icon: '📦', label: 'Source Control' },
    { id: 'debug', icon: '🐛', label: 'Run and Debug' },
    { id: 'extensions', icon: '🧩', label: 'Extensions' }
  ];

  let activeView: string = 'explorer';
  let isSideBarVisible = true;
</script>

<div class="sidebar-container">
  <!-- Activity Bar -->
  <div class="activity-bar">
    {#each activities as item}
      <button
        class:active={activeView === item.id}
        onclick={() => {
          if (activeView === item.id) {
            isSideBarVisible = !isSideBarVisible;
          } else {
            activeView = item.id;
            isSideBarVisible = true;
          }
        }}
        title={item.label}
      >
        <span class="icon">{item.icon}</span>
      </button>
    {/each}
  </div>

  <!-- Side Bar -->
  {#if isSideBarVisible}
    <div class="side-bar">
      <div class="side-bar-title">
        {activities.find(item => item.id === activeView)?.label}
      </div>
      <div class="side-bar-content">
        <!-- Content changes based on activeView -->
        {#if activeView === 'explorer'}
          <div class="section">
            <div class="section-title">OPEN EDITORS</div>
            <!-- Add editor list here -->
          </div>
          <div class="section">
            <div class="section-title">PROJECT NAME</div>
            <!-- Add file tree here -->
          </div>
        {/if}
      </div>
    </div>
  {/if}
</div>

<style>
  .sidebar-container {
    display: flex;
    height: 100%;
  }

  .activity-bar {
    width: 48px;
    background: #333333;
    display: flex;
    flex-direction: column;
    padding: 8px 0;
  }

  .activity-bar button {
    width: 48px;
    height: 48px;
    display: flex;
    justify-content: center;
    align-items: center;
    background: none;
    border: none;
    color: #858585;
    cursor: pointer;
    position: relative;
  }

  .activity-bar button:hover {
    color: #ffffff;
  }

  .activity-bar button.active {
    color: #ffffff;
  }

  .activity-bar button.active::before {
    content: '';
    position: absolute;
    left: 0;
    width: 2px;
    height: 100%;
    background: #ffffff;
  }

  .side-bar {
    width: 300px;
    background: #252526;
    display: flex;
    flex-direction: column;
  }

  .side-bar-title {
    padding: 10px 20px;
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    background: #252526;
    border-bottom: 1px solid #333333;
  }

  .side-bar-content {
    flex: 1;
    overflow-y: auto;
  }

  .section {
    padding: 10px 0;
  }

  .section-title {
    padding: 4px 12px;
    font-size: 11px;
    font-weight: 600;
    color: #858585;
  }

  /* For the icons, you might want to use a proper icon library instead of emojis */
  .icon {
    font-size: 24px;
  }
</style> 