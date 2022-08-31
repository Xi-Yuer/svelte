<script>
  export let steps = ['步骤一', '步骤二', '步骤三', '步骤四']
  export let current = 1
  let currentStep = current - 1
</script>

<div class="content">
  {#each steps as step, index}
    <div class="step" class:active={currentStep === index}>
      <slot name="step" {step} {index}>
        <div class="stepItem">
          <span class="stepIndex" class:stepItemActive={currentStep >= index}
            >{index + 1}</span
          >
          <span class="StepName" class:StepNameActive={currentStep >= index}
            >{step}</span
          >
        </div>
      </slot>
      <span
        class:line={steps.length - 1 !== index}
        class:active-line={currentStep > index}
      />
    </div>
  {/each}
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .active {
    color: #409eff;
  }
  .active-line {
    background-color: #409eff !important;
  }
  .content {
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
  .step {
    flex: 1;
    position: relative;
  }
  .line {
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #686868;
    top: 50%;
    z-index: -1;
    margin-top: -7px;
    transform: translateY(-50%);
  }
  .stepItem {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .stepIndex {
    display: inline-block;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    border: 2px solid #686868;
    background-color: white;
  }
  .StepNameActive {
    color: #409eff;
  }
  .stepItemActive {
    border: 2px solid #409eff;
    color: #409eff;
  }
</style>
