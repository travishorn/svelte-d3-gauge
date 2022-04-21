<script>
  import { select } from "d3-selection";
  import { arc } from "d3-shape";
  import { onMount } from "svelte";

  export let min = 0;
  export let max = 100;
  export let slices;
  export let value;

  const chartId = `chart-${crypto.randomUUID()}`;
  const width = 200;
  const height = 200;
  const viewBox = [0, 0, width, height - height / 4].join(" ");

  const arcGenerator = arc();

  const angle = (x) => -0.5 * Math.PI + ((x - min) / (max - min)) * Math.PI;

  onMount(() => {
    const svg = select(`#${chartId}`);
    const chart = svg
      .append("g")
      .attr("transform", `translate(${width / 2} ${height / 2})`);

    chart
      .selectAll(".slice")
      .data(slices)
      .join("path")
      .attr("class", "slice")
      .attr("fill", (d) => d.color)
      .attr("d", (d) =>
        arcGenerator({
          startAngle: angle(d.from),
          endAngle: angle(d.to),
          innerRadius: 33.3,
          outerRadius: 100,
        })
      );

    chart
      .append("path")
      .attr("class", "needlePoint")
      .attr("fill", "#616161")
      .attr("d", "M 0 0 L 0 6 L -50 0 L 0 -6 Z")
      .attr("transform", `rotate(${((value - min) / (max - min)) * 180})`);

    chart
      .append("circle")
      .attr("class", "needleBase")
      .attr("fill", "#616161")
      .attr("r", 7);

    chart
      .append("text")
      .attr("class", "value")
      .text(value)
      .attr("font-size", "35")
      .attr("font-family", "Arial, Helvetica, sans-serif")
      .attr("text-anchor", "middle")
      .attr("fill", "#616161")
      .attr("y", 40);
  });
</script>

<svg id={chartId} {viewBox} />
