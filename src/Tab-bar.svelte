<script>
  import { push } from 'svelte-spa-router'
  export let tabList = []

  let currentIndex = 0

  const tabItemClick = (path, index) => {
    currentIndex = index
    push(path)
  }
</script>

<div class="container flex">
  <div class="content flex">
    {#each tabList as { title, path }, index}
      <!-- 动态属性 class -->
      <div
        on:click={() => tabItemClick(path, index)}
        class:active={currentIndex === index}
      >
        {title}
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
