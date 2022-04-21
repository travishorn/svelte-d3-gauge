<script>
  import ChartGauge from "./lib/ChartGauge.svelte";

  const min = 0;
  const max = 100;
  const value = 50;

  const slices = [
    { color: "#E43836", from: 0, to: 20 },
    { color: "#F06D03", from: 20, to: 40 },
    { color: "#FFC10A", from: 40, to: 60 },
    { color: "#CDDC39", from: 60, to: 80 },
    { color: "#8EC44C", from: 80, to: 100 },
  ];
</script>

<div class="container">
  <ChartGauge {min} {max} {value} {slices} />
</div>

<style>
  .container {
    max-width: 500px;
    margin: 5rem auto;
  }
</style>
