<script>
  export let githubName;
  export let branchName;
</script>

<h2>Setup</h2>
<ol>
  <li>
    <p>
      Ensure you have the <a
        href="https://review.docs.microsoft.com/en-us/help/contribute/contribute-get-started-setup-github?branch=master"
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
    <p>Add a remote named <code>upstream</code>:</p>
    <pre><code>git remote add upstream http://github.com/MicrosoftDocs/azure-docs-pr.git</code></pre>
  </li>
  <li>
    <p>Fetch the release branch:</p>
    <pre><code>git fetch upstream {branchName}</code></pre>
  </li>
  <li>
    <p>Create your local branch:</p>
    <pre><code>git checkout -B {branchName} upstream/{branchName}</code></pre>
  </li>
  <li>
    <p>Work off custom branches:</p>
    <pre><code>git checkout -B &lt;ARTICLE_BRANCH_NAME&gt; {branchName}</code></pre>
  </li>
</ol>

<style>
  ol li {
    margin-top: 1.75em;
  }
</style>
