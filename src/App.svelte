<script>
  const GITHUB_NAME_DEFAULT = "<GITHUB_USER_NAME>";
  const BRANCH_NAME_DEFAULT = "<BRANCH_NAME>";

  let githubName = GITHUB_NAME_DEFAULT;
  let branchName = BRANCH_NAME_DEFAULT;

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

  function setQueryValue() {
    const params = [];

    if (githubName !== GITHUB_NAME_DEFAULT) {
      params.push(`user=${githubName}`);
    }

    if (branchName !== BRANCH_NAME_DEFAULT) {
      params.push(`branch=${branchName}`);
    }

    if (params.length > 0) {
      const url = `${window.location.origin}?${params.join("&")}`;
      window.history.pushState(null, "Branch Buddy", url);
    }
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
  <p class="has-text-centered">
    Check out the
    <a
      href="https://review.docs.microsoft.com/en-us/help/contribute/contribute-quick-reference?branch=master"
      target="_blank">quick reference</a
    > for help with common docs-related tasks.
  </p>

  <hr />

  <div class="columns">
    <div class="column is-one-fifth">
      <label
        for="github-name"
        class="mt-2 has-text-weight-semibold has-text-right"
        >GitHub username:</label
      >
    </div>
    <div class="column">
      <input
        type="text"
        name="github-name"
        id="github-name"
        class="input"
        on:input={(e) => {
          let value = e.currentTarget.value;
          githubName = value.length > 0 ? value : GITHUB_NAME_DEFAULT;
        }}
        on:blur={(e) => setQueryValue()}
      />
    </div>
  </div>
  <div class="columns">
    <div class="column is-one-fifth">
      <label
        for="branch-name"
        class="mt-2 has-text-weight-semibold has-text-right">Branch name:</label
      >
    </div>
    <div class="column">
      <input
        type="text"
        name="branch-name"
        id="branch-name"
        class="input"
        on:input={(e) => {
          let value = e.currentTarget.value;
          branchName = value.length > 0 ? value : BRANCH_NAME_DEFAULT;
        }}
        on:blur={(e) => setQueryValue()}
      />
    </div>
  </div>

  <hr />

  <h2>Setup</h2>
  <ol>
    <li>
      <p>
        Ensure you have the <a
          href="https://review.docs.microsoft.com/en-us/help/contribute/contribute-get-started-setup-github?branch=master"
          target="_blank">right GitHub permissions</a
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
      <pre><code>git checkout -B &lt;ARTICLE_BRANCH_NAME&gt; {branchName}</code></pre>
    </li>
  </ol>

  <h2>Maintenance</h2>
  <p>
    Do this once a day to keep your local branch(es) up to date with the server
    branch.
  </p>
  <pre><code>git pull upstream {branchName}</code></pre>
</main>

<style>
  ol li {
    margin-top: 1.75em;
  }

  main {
    padding-bottom: 6em;
  }
</style>
