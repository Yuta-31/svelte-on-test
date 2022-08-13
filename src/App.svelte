<svelte:head>
	<title>Multiple Counter</title>
</svelte:head>

<main>
  <center>
    <div class="title">Multiple Counter</div>
    {#each counters as counter (counter.id)}
      <CounterCard
        bind:title={counter.title}
        bind:count={counter.count}
        remove={() => {
          removeCounter(counter.id);
        }}
      />
    {/each}
    <div on:click={() => addNewCounter("new", 0)} class="new-counter-button">
      new counter
    </div>
    <div>
      title list:
      {#each counters as counter (counter.id)}
        {#if lastIdx == counter.id}
          {counter.title}&nbsp;
        {:else}
          {counter.title},&nbsp;
        {/if}
      {/each}
    </div>
    <div>
      sum of count: {sumOfCount}
    </div>
  </center>
</main>

<script lang="ts">
	import CounterCard from "./components/CounterCard.svelte";
  
	let id: number = 1;
	type Counter = {
	  id: number;
	  title: string;
	  count: number;
	};
  
	let counters: Counter[] = [{ id: 0, title: "new", count: 0 }];
	const addNewCounter = (title: string, count: number) => {
	  counters = [...counters, { id, title, count }];
	  id += 1;
	};
	const removeCounter = (id: number) => {
	  counters = counters.filter((counter) => counter.id !== id);
	};
	$: sumOfCount = counters.reduce(
	  (total: number, counter: Counter): number => total + counter.count,
	  0
	);
	$: lastIdx = counters.reduce((lastIdx: number, counter: Counter): number => {
	  if (lastIdx < counter.id) {
		return counter.id;
	  } else {
		return lastIdx;
	  }
	}, 0);
	$: console.log(counters, lastIdx);
  </script>

<style>
  .title {
    font-weight: 400;
    font-size: 4rem;
    margin-bottom: 10px;
  }
  .new-counter-button {
    background-color: #68d391;
    color: white;
    border: none;
    border-radius: 5px;
    width: 384px;
    height: 24px;
    cursor: pointer;
    line-height: 24px;
  }
</style>
