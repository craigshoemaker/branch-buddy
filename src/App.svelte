<script>
  import Maintenance from "./Maintenance.svelte";
  import PullRequests from "./PullRequests.svelte";
  import CreateBranch from "./CreateBranch.svelte";
  import Setup from "./Setup.svelte";

  const GITHUB_NAME_DEFAULT = "<GITHUB_USER_NAME>";
  const BRANCH_NAME_DEFAULT = "<RELEASE_BRANCH_NAME>";
  const BRANCH_NAME_LOCAL_DEFAULT = "<LOCAL_ARTICLE_BRANCH_NAME>";

  let githubName = GITHUB_NAME_DEFAULT;
  let branchName = BRANCH_NAME_DEFAULT;
  let branchNameLocal = BRANCH_NAME_LOCAL_DEFAULT;

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

    if (branchNameLocal !== BRANCH_NAME_LOCAL_DEFAULT) {
      params.push(`local-branch=${branchNameLocal}`);
    }

    const hasParamsToAdd = params.length > 0;
    let url = window.location.href;

    if (hasParamsToAdd) {
      url += `?${params.join("&")}`;
      window.history.pushState(null, window.document.title, url);
    }

    window.history.pushState(null, window.document.title, url);
  }

  window.addEventListener("DOMContentLoaded", () => {
    if (window.location.search) {
      let branch = getQueryValue("branch");
      let user = getQueryValue("user");
      let localBranch = getQueryValue("local-branch");

      if (branch) {
        branchName = branch;
        document.getElementById("branch-name").value = branch;
      }

      if (user) {
        githubName = user;
        document.getElementById("github-name").value = user;
      }

      if (localBranch) {
        branchNameLocal = localBranch;
        document.getElementById("branch-name-local").value = localBranch;
      }
    }
  });
</script>

<main class="container content mt-6">
  <h1 class="has-text-centered">🌿 Branch Buddy 🌿</h1>

  <hr />

  <div class="columns">
    <div class="column is-one-fifth">
      <label
        for="github-name"
        class="mt-2 has-text-weight-semibold has-text-right-desktop has-text-centered-mobile"
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
          let value = e.currentTarget.value.trim();
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
        class="mt-2 has-text-weight-semibold  has-text-right-desktop has-text-centered-mobile"
        >Remote branch name:</label
      >
    </div>
    <div class="column">
      <input
        type="text"
        name="branch-name"
        id="branch-name"
        class="input"
        on:input={(e) => {
          let value = e.currentTarget.value.trim();
          branchName = value.length > 0 ? value : BRANCH_NAME_DEFAULT;
        }}
        on:blur={(e) => setQueryValue()}
      />
    </div>
  </div>
  <div class="columns">
    <div class="column is-one-fifth">
      <label
        for="branch-name"
        class="mt-2 has-text-weight-semibold  has-text-right-desktop has-text-centered-mobile"
        >Local branch name:</label
      >
    </div>
    <div class="column">
      <input
        type="text"
        name="branch-name-local"
        id="branch-name-local"
        class="input"
        on:input={(e) => {
          let value = e.currentTarget.value.trim();
          branchNameLocal =
            value.length > 0 ? value : BRANCH_NAME_LOCAL_DEFAULT;
        }}
        on:blur={(e) => setQueryValue()}
      />
    </div>
  </div>

  <hr />

  <Setup {githubName} {branchNameLocal} {branchName} />
  <CreateBranch {githubName} {branchNameLocal} {branchName} />
  <PullRequests {githubName} {branchNameLocal} {branchName} />
  <Maintenance {branchName} {branchNameLocal} />
</main>

<style>
  main {
    padding-bottom: 6em;
  }

  h1 {
    letter-spacing: -0.08em;
  }
</style>
