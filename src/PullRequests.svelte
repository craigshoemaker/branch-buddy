<script>
  export let branchNameLocal;
  export let branchName;
  export let githubName;
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
  <ol>
    <li>
      <p>Push your local branch to your fork on GitHub.</p>
      <pre><code>git push origin {branchNameLocal}</code></pre>
    </li>
    {#if !/\>/.test(branchNameLocal)}
      <li>
        <p>Click this button to open GitHub in the browser.</p>
        <p>
          <a
            class="button"
            target="_blank"
            href="https://github.com/{githubName}/azure-docs-pr/pull/new/{branchNameLocal}"
            >Start a pull request</a
          >
        </p>
      </li>
    {:else}
      <li><p>Navigate to the branch on GitHub and start a pull request.</p></li>
    {/if}
    <li>
      <p>
        Change the branch name of the <strong>base repository</strong> to point
        to the <code>{branchName}</code> branch.
      </p>
    </li>
    <li>
      <p>Click the <strong>Create pull request</strong> button.</p>
    </li>
  </ol>
</details>

<style>
  a.button {
    background-color: #dcf5ff;
    font-weight: 600;
  }
</style>
