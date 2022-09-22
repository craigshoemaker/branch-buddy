<script>
  export let branchName;
  export let branchNameLocal;
</script>

<details>
  <summary>
    <h2>Maintenance</h2>
  </summary>
  <p>Daily synchronize your local branch with the remote branch.</p>
  <ol>
    <li>
      <pre><code>git checkout {branchNameLocal}</code></pre>
      <pre><code>git pull upstream {branchName}</code></pre>
    </li>
  </ol>
</details>
