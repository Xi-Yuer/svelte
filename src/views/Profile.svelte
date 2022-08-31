<script>
  import Steps from '../components/steps/index.svelte'
</script>

<h2>Profile</h2>
<h2>插槽step</h2>
<div class="profile">
  <Steps current={3} let:step>
    <button slot="step">{step}</button>
  </Steps>
</div>
<br>
<h2>默认step</h2>
<div class="profile">
  <Steps current={3} />
</div>

<style>
  .profile {
    width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
