# AI Prompt configuration bootstrap

Use this prompt from within the target repository to apply the changes required to make it a grant configuration repository.

---

Compare this repository with the bootstrap repository:

https://github.com/DEFRA/grants-config-bootstrap

Tasks:
1. Add bootstrap's ./docs/README.md to ./README.md, put 'Grant Configuration' as the first section, but after section links.
2. Update package.json
   a. npm install dev dependencies, @changesets/cli @changesets/changelog-github.
   b. npm install dependencies using min-release-age=0, @defra/grants-config-utils.
   C. add bootstrap's ./npm/package.json to ./package.json, keeping existing scripts, replacing $TARGET_REPO_NAME$ with name field, new fields added to end of section.
3. Setup changesets
   a. initialise changeset using npx
   b. add bootstrap's ./changeset/pr-changeset-check.yml to ./.github/workflows/
4. Setup husky
   a. npm run setup:husky
   b. append bootstrap's ./husky/pre-commit to ./.husky/pre-commit