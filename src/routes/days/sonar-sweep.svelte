<script>
  import { measurements } from '$lib/stores/measurements';

  /** 
   * O(n-1)
  */
  const findDescents = (arr) => {
    let total = 0;
    // we start at index 1 since 0 has no previous measurement
    for (let i = 1; i < arr.length; i++) {
      if (+arr[i - 1] > +arr[i]) continue;
      total++;
    }
    return total;
  }

  $: totalDescents = findDescents($measurements);

  /**
   * O(n)
  */
  const slidingWindow = (arr, range) => {
    let total = 0;
    let curValue = 0;

    for (let i = 0; i < arr.length; i++) {
      // we don't compare until we've accumulated the range amt of numbers
      if (i < range) {
        curValue += arr[i];
        continue;
      }

      const prevValue = curValue;
      // remove the oldest number of the 3 then add the number at current index
      curValue -= arr[i - range] - arr[i];

      if (prevValue < curValue) total++;
    }

    return total;
  }

  $: slidingWindowCount = slidingWindow($measurements, 3);
</script>

<h2>Day 1: Sonar Sweep</h2>

<p>
  How many measurements are larger than the previous measurement?
</p>

<p>Part 1: {totalDescents} descents</p>

<p>Part 2: {slidingWindowCount} descents</p>