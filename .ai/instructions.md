# AI Prompt configuration bootstrap

Use this prompt from within the target repository to apply the changes required to make it a grant configuration repository.

---

Compare this repository with the bootstrap repository:

https://github.com/DEFRA/grants-config-bootstrap

Tasks:
1. Add bootstrap's ./docs/README.md to ./README.md, put 'Grant Configuration' as the first section, but after section links.
2. Update package.json
   - npm install dev dependencies, @changesets/cli @changesets/changelog-github.
   - npm install dependency using min-release-age=0, @defra/grants-config-utils.
   - add bootstrap's ./npm/package.json to ./package.json, keeping existing scripts, replacing $TARGET_REPO_NAME$ with name field, new fields added to end of section.
3. Setup changesets
   - initialise changeset using npx
   - add bootstrap's ./changeset/pr-changeset-check.yml to ./.github/workflows/
4. Setup husky
   - npm run setup:husky
   - append bootstrap's ./husky/pre-commit to ./.husky/pre-commit
5. Update service publishing
   - copy bootstrap's ./publish/release-it.sh to ./ci/release-it.sh, grant execute permissions
   - merge the snippets from bootstrap's ./publish/publish.yml into ./.github/workflows/publish.yml, don't replace the name field
6. Make code changes to support configuration repo
   - create directory ./configurations
   - remove ./src/routes/example.js and its usages
   - merge storeConfigVersionAndInformBroker from bootstrap's ./code-changes/start-server.js into ./src/common/start-server.js
   - merge storeConfigVersionAndInformBroker from bootstrap's ./code-changes/start-server.test.js into ./src/common/start-server.test.js
7. Configure for local running 
   - update aws.env AWS_ENDPOINT_URL, swap localhost for floci
   - merge the snippets from bootstrap's ./local-running/compose.yml into ./compose.yml, note bootstrap's $TARGET_REPO_SPECIFIC$ signifies a variable
   - update 10-setup-resources.sh, add configs-bucket create command
   - merge the snippets from bootstrap's ./local-running/Dockerfile into ./Dockerfile
   - copy bootstrap's ./local-running/start to ./scripts/start, grant execute permissions
   - copy bootstrap's ./local-running/.env to ./.env
8. Update sonar-project.properties to exclude src/index.js and src/routes/health.js