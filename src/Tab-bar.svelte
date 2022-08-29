<script>
  import { push } from 'svelte-spa-router'
  export let tabList = []

  let currentIndex = 0

  const tabItemClick = (tabItem, index) => {
    currentIndex = index
    push(tabItem.path)
  }
</script>

<div class="container flex">
  <div class="content flex">
    {#each tabList as tabItem}
      <!-- 动态属性 class -->
      <div
        on:click={() => tabItemClick(tabItem, tabList.indexOf(tabItem))}
        class:active={currentIndex === tabList.indexOf(tabItem)}
      >
        {tabItem.title}
      </div>
    {/each}
  </div>
</div>

<style>
  .flex {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .container {
    height: 40px;
  }
  .container .content {
    width: 800px;
    height: 100%;
    margin: 0 auto;
    text-align: center;
    cursor: pointer;
  }
  .content div {
    flex: 1;
  }
  .active {
    color: orange;
  }
</style>
