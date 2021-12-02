<script>
  import '$lib/styles/global.scss';
</script>

<h1>Keith's Advent of Code</h1>

<nav>
  Day
  <a href="/days/sonar-sweep">1</a> |
  <a href="/days/dive">2</a>
</nav>
<slot/>

<style lang="scss">
  nav a {
    text-decoration: none;

    &:hover {
      text-decoration: underline;
    }
  }
</style>