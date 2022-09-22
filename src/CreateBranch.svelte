<script>
  export let githubName;
  export let branchName;
  export let branchNameLocal;
</script>

<details>
  <summary>
    <h2>Create a local branch</h2>
  </summary>
  <ol>
    <li>
      <p>Fetch the server branch:</p>
      <pre><code>git fetch upstream {branchName}</code></pre>
    </li>
    <li>
      <p>Create your local branch:</p>
      <pre><code>git checkout -B {branchName} upstream/{branchName}</code></pre>
    </li>
  </ol>
</details>

<style>
  ol li {
    margin-top: 1.75em;
  }
</style>
