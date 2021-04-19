<script>
  export let branchNameLocal;
</script>

<details>
  <summary>
    <h2>Pull Requests</h2>
  </summary>
  <p>
    Create a pull request by pushing your local branch to GitHub and then
    issuing a <a
      href="https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests"
      tabindex="-1"
      target="_blank">pull request</a
    >.
  </p>
  <hr />
  <p>Copy your local branch to your fork on GitHub.</p>
  <pre><code>git push origin {branchNameLocal}</code></pre>

  {#if !/\>/.test(branchNameLocal)}
    <p>Click this button to start your pull request.</p>
    <p>
      <a
        class="button"
        target="_blank"
        href="https://github.com/craigshoemaker/azure-docs-pr/pull/new/{branchNameLocal}"
        >Start a pull request</a
      >
    </p>
  {:else}
    <p>Navigate to the branch on GitHub and start a pull request.</p>
  {/if}
</details>

<style>
  a.button {
    background-color: #dcf5ff;
    font-weight: 600;
  }
</style>
