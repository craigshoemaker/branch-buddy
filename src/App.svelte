<script>
  export let githubName = "<GITHUB_USER_NAME>";
  export let branchName = "<BRANCH_NAME>";

  function getQueryValue(key) {
    let query = window.location.search.replace("?", "");
    let values = query.split("&");
    let value = "";
    for (let i = 0; i < values.length; i++) {
      let [match, k, v] = values[i].match(/(.*)\=(.*)/);
      if (key === k) {
        value = v;
        break;
      }
    }
    return value;
  }

  window.addEventListener("DOMContentLoaded", () => {
    if (window.location.search) {
      let branch = getQueryValue("branch");
      let user = getQueryValue("user");

      if (branch) {
        branchName = branch;
        document.getElementById("branch-name").value = branch;
      }

      if (user) {
        githubName = user;
        document.getElementById("github-name").value = user;
      }
    }
  });
</script>

<main class="container content mt-6">
  <h1 class="has-text-centered">🌿 Branch Buddy 🌿</h1>
  <div class="columns">
    <div class="column is-one-fifth">
      <label for="github-name" class="mt-5 has-text-weight-semibold"
        >GitHub username:</label
      >
    </div>
    <div class="column">
      <input
        type="text"
        name="github-name"
        id="github-name"
        class="input m-4"
        placeholder="GitHub username"
        on:input={(e) => (githubName = e.currentTarget.value)}
      />
    </div>
  </div>
  <div class="columns">
    <div class="column is-one-fifth">
      <label for="branch-name" class="mt-5 has-text-weight-semibold"
        >Branch name:</label
      >
    </div>
    <div class="column">
      <input
        type="text"
        name="branch-name"
        id="branch-name"
        class="input m-4"
        placeholder="branch name"
        on:input={(e) => (branchName = e.currentTarget.value)}
      />
    </div>
  </div>

  <hr />

  <ol>
    <li>
      <p>
        Ensure you have the <a
          href="https://review.docs.microsoft.com/en-us/help/contribute/contribute-get-started-setup-github?branch=master"
          target="_blank">right permissions</a
        >
      </p>
    </li>
    <li>
      <p>
        Fork the <a href="http://github.com/MicrosoftDocs/azure-docs-pr"
          >azure-docs-pr</a
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
      <pre><code>git checkout {branchName}</code></pre>
      <pre><code>git checkout -b &lt;BRANCH_NAME&gt;</code></pre>
    </li>
  </ol>

  <hr />

  <blockquote>
    <p>
      <strong>Note:</strong> Check out the
      <a
        href="https://review.docs.microsoft.com/en-us/help/contribute/contribute-quick-reference?branch=master"
        rel="nofollow">quick reference</a
      > for help with common tasks.
    </p>
  </blockquote>
</main>

<style>
  ol * {
    font-size: 1.02em;
  }
</style>
