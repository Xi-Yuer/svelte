<script>
  let count = 0
  // 计算属性
  $: doubleCount = count * 2

  const increment = () => {
    count++
  }
  const decrement = () => {
    count--
  }
  // 自动收集依赖，发生变化执行该代码块
  $: {
    console.log('count发生了变化', count)
  }
</script>

<h2>Home</h2>
<span>count:{count}</span>
<br />
<span>doubleCount:{doubleCount}</span>
<br />
<button on:click={increment}>+</button>
<button on:click={decrement}>-</button>
