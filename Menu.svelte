<script>
  let scoops = 1;
  let menu = ["chocolate", "vanillla", "butterscotch"];
  let flavors = [];
  $: console.log(flavors);
  function getSelectedFlavors(flavors) {
    if (flavors.length === 1) return flavors[0];
    return `${flavors.slice(0, -1).join(",")} and ${flavors[flavors.length - 1]}`;
  }
</script>

<div class="main-container">
  <div class="menu-container">
    <label class="num-scoops">
      <input type="radio" bind:group={scoops} value={1}>
      One scoop
    </label>
    <label class="num-scoops">
      <input type="radio" bind:group={scoops} value={2}>
      Two scoops
    </label>
    <label class="num-scoops">
      <input type="radio" bind:group={scoops} value={3}>
      Three scoops
    </label>
  </div>
  <div class="flavors">
    {#each menu as flavor}
      <label>
        <input type="checkbox" bind:group={flavors} value={flavor} name={flavor}/>
        {flavor}
      </label>
    {/each}
  </div>
  {#if flavors.length===0}
  <h1 class="order-not-set"> Choose a Flavor </h1>
  {:else}
  <h1 class="order-details"> you selected {scoops} {scoops === 1 ? "scoop" : "scoops"} of {getSelectedFlavors(flavors)}</h1>
  {/if}
  <button class="order-btn"> ORDER </button>
</div>

<style>
  .main-container {
    display: flex;
    flex-flow: column;
    align-self: center;
  }
  .menu-container {
    padding: 2em;
    align-self: center;
    position: relative;
    display: flex;
    flex-flow: row;
  }
  .num-scoops {
    padding: 0.5em;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  }
  .order-details {
    text-align: center;
    color: blue;
    font-size: 2em;
  }
  .order-not-set {
    color: red;
    font-size: 2em;
  }
  .order-btn {
    align-self: center;
    padding: 0.5em 1.5em;
    border-radius: 0.3em;
    background-color: yellow;
  }
</style>