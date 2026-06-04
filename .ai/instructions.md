# AI Prompt configuration bootstrap

Use this prompt from within the target repository to apply the changes required to make it a grant configuration repository.

---

Compare this repository with the bootstrap repository:

https://github.com/DEFRA/grants-config-bootstrap

Tasks:
1. Add bootstrap's ./docs/README.md to ./README.md, put 'Grant Configuration' as the first section, but after section links.
2. Update package.json
   a. npm install dev dependencies, @changesets/cli @changesets/changelog-github.
   b. npm install dependency using min-release-age=0, @defra/grants-config-utils.
   C. add bootstrap's ./npm/package.json to ./package.json, keeping existing scripts, replacing $TARGET_REPO_NAME$ with name field, new fields added to end of section.
3. Setup changesets
   a. initialise changeset using npx
   b. add bootstrap's ./changeset/pr-changeset-check.yml to ./.github/workflows/
4. Setup husky
   a. npm run setup:husky
   b. append bootstrap's ./husky/pre-commit to ./.husky/pre-commit
5. Update service publishing
   a. copy bootstrap's ./publish/release-it.sh to ./ci/release-it.sh, grant execute permissions
   b. merge the snippets from bootstrap's ./publish/publish.yml into ./.github/workflows/publish.yml
6. Make code changes to support configuration repo
   a. create directory ./configurations
   b. remove ./src/routes/example.js and its usages
   c. merge storeConfigVersionAndInformBroker from bootstrap's ./code-changes/start-server.js into ./src/common/start-server.js
   d. merge storeConfigVersionAndInformBroker from bootstrap's ./code-changes/start-server.test.js into ./src/common/start-server.test.js
7. Configure for local running 
   a. update aws.env AWS_ENDPOINT_URL, swap localhost for floci
   b. merge the snippets from bootstrap's ./local-running/compose.yml into ./compose.yml, note bootstrap's $TARGET_REPO_SPECIFIC$ signifies a variable
   c. update 10-setup-resources.sh, add configs-bucket create command
   d. merge the snippets from bootstrap's ./local-running/Dockerfile into ./Dockerfile
   e. copy bootstrap's ./local-running/start to ./scripts/start, grant execute permissions
   f. copy bootstrap's ./local-running/.env to ./.env
8. Update sonar-project.properties to exclude src/index.js and src/routes/health.js