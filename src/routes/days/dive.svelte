<script>
  import { directions } from '$lib/stores/sub-chart';

  const coords = { x: 0, y: 0 }

  $: {
    $directions.forEach((dir) => {
      const [d, v] = dir.split(/\s+/);

      if (d.includes('forward')) {
        coords.x += +v;
        return;
      }
      if (d.includes('up')) {
        coords.y -= +v;
        return;
      }

      coords.y += +v;
    })
  }
</script>

<h2>Day 2: Dive!</h2>

<p>Step 1: {coords.x * coords.y}</p>

<p>Step 2: WIP...</p>