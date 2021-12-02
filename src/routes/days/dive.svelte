<script>
  import { directions } from '$lib/stores/sub-chart';

  const coords = { x: 0, y: 0 }

  $: {
    $directions.forEach((dir) => {
      debugger;
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

<p>Work in progress...{coords.x * coords.y}</p>