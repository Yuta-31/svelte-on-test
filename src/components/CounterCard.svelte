<script lang="ts">
  export let count: number = 0;
  export let title: string = "new";
  export let remove: () => void;

  const increment = () => {
    count += 1;
  };
  const decrement = () => {
    if (count > 0) count -= 1;
  };
  const setZero = () => {
    count = 0;
  };
</script>

<div class="counter">
  <input type="text" name="title" bind:value={title} />
  <span>{count}</span>
  <div class="button inc" on:click={increment}>+</div>
  <div class="button dec" on:click={decrement}>-</div>
  <div class="button zero" on:click={setZero}>0</div>
  <div class="button x" on:click={remove}>x</div>
</div>

<style>
  .counter {
    width: 384px;
    height: 43px;
    margin: 0 0 0.5rem 0;
    border-radius: 3px;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.24);
    background-color: #f7fafc;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .counter input {
    border: none;
    width: 128px;
    height: 24px;
    margin-top: 10px;
    margin-left: 16px;
    margin-right: 26px;
    color: gray;
  }

  .counter span {
    width: 44px;
    height: 27px;
    margin-right: 35px;
    padding-top: 7px;
    font-weight: bold;
    font-size: 1.125rem;
  }

  .counter .button {
    width: 35px;
    height: 35px;
    border: none;
    color: white;
    font-size: 1.125rem;
    cursor: pointer;
    line-height: 35px;
  }
  .counter .inc {
    background-color: #f56565;
    border-radius: 5px 0 0 5px;
  }
  .counter .dec {
    background-color: #4299e1;
    border-radius: 0;
  }
  .counter .zero {
    background-color: #ecc94b;
    border-radius: 0 5px 5px 0;
  }
  .counter .x {
    background-color: none;
    color: gray;
  }
</style>
