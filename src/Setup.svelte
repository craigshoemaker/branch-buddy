<script>
  export let githubName;
  export let branchName;
  export let branchNameLocal;
</script>

<details>
  <summary>
    <h2>Setup</h2>
  </summary>
  <ol>
    <li>
      <p>
        Ensure you have the <a
          href="https://review.learn.microsoft.com/en-us/help/get-started/setup-github"
          target="_blank"
          tabindex="-1">right GitHub permissions</a
        >
      </p>
    </li>
    <li>
      <p>
        Fork the <a
          href="http://github.com/MicrosoftDocs/azure-docs-pr"
          tabindex="-1">azure-docs-pr</a
        > repository
      </p>
    </li>
    <li>
      <p>Clone the fork to your machine:</p>
      <pre><code>git clone https://github.com/{githubName}/azure-docs-pr.git</code></pre>
    </li>
    <li>
      <p>Change into the folder created for the repository.</p>
      <pre><code>cd azure-docs-pr</code></pre>
    </li>
    <li>
      <p>Add a remote named <code>upstream</code>:</p>
      <pre><code>git remote add upstream http://github.com/MicrosoftDocs/azure-docs-pr.git</code></pre>
    </li>
  </ol>
</details>

<style>
  ol li {
    margin-top: 1.75em;
  }
</style>
