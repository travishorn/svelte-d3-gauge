# Svelte D3 Gauge

A Svelte component for rendering a gauge chart.

![A gauge chart showing 5 equal slices colored red to green. The needle is
pointing straight up. The number 50 appears below the chart.](./example.png)

## Usage

Make sure D3 is installed

```bash
npm install d3
```

Import `./src/lib/ChartGauge.svelte` in your project and set its options.

```svelte
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
```

## Example Server

Clone this repository

```bash
git clone https://github.com/travishorn/svelte-d3-gauge
```

Change into the directory

```bash
cd svelte-d3-gauge
```

Install dependencies

```bash
npm install
```

Run development server

```bash
npm run dev
```

Navigate to http://localhost:3000

Change the options in `./src/App.svelte`. The chart will be hot-reloaded in your
browser.

## License

The MIT License (MIT)

Copyright © 2022 Travis Horn

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the “Software”), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
