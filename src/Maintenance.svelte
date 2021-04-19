<script>
  export let branchName;
  export let branchNameLocal;
</script>

<details>
  <summary>
    <h2>Maintenance</h2>
  </summary>
  <p>Daily synchronize your local branches with the server branch.</p>
  <ol>
    <li>
      <p>Sync your local release branch.</p>
      <pre><code>git checkout {branchName}</code></pre>
      <pre><code>git pull upstream {branchName}</code></pre>
    </li>
    <li>
      <p>Sync your article branch.</p>
      <pre><code>git checkout {branchNameLocal}</code></pre>
      <pre><code>git pull upstream {branchName}</code></pre>
    </li>
  </ol>
</details>
