## Grant Configuration

### Create new

Each directory within the `configurations` folder represents a separate grant.

To create a new grant:

1. Create a new directory under `configurations`, for example:

   ```text
   configurations/playground
   ```

2. Add at least one configuration file, for example:

   ```text
   configurations/playground/slide-config/main.json
   ```

3. Create a new version:

   ```bash
   npm run version
   ```

4. Stage and commit your changes using the standard commit format:

   ```bash
   git add .
   git commit -m "feat(YOUR-TICKET): YOUR-MESSAGE"
   ```

5. Push your branch and then follow the standard GitHub pull request process.

   ```bash
   git push
   ```

### Update existing

To update the configuration for an existing grant:

1. Add or modify the required configuration files.

2. Create a new version:

   ```bash
   npm run version
   ```

3. Stage and commit your changes:

   ```bash
   git add .
   git commit -m "feat(YOUR-TICKET): YOUR-MESSAGE"
   ```

4. Push your branch and then follow the standard GitHub pull request process.

   ```bash
   git push
   ```

### Non-configuration changes

Any change that does not modify the contents of the `configurations` directory is considered a **non-configuration change**.

Do **not** create a changeset for these changes. Non-configuration changes do not trigger service publication when merged into `main`.

### Hotfix Releases

Hotfix releases should only be used as a last resort when a fix cannot be delivered through the normal release process because subsequent releases contain incompatible changes.

> **Important:** Changes made on a hotfix branch are not automatically included in future releases. After publishing the hotfix, apply the same changes to `main` to ensure they are included in the next release.

Hotfix releases can only increment the **patch** version of an existing release.

If a hotfix is required, complete the following steps:

1. Create a hotfix branch from the tagged release version that requires the fix. For example, the following command creates a `hotfix-releases/6.3.x` branch from the `6.3.0` tag:

   ```bash
   git fetch --tags
   git switch -c hotfix-releases/6.3.x tags/6.3.0
   ```

2. Make the required configuration changes.

3. Create a new patch version:

   ```bash
   npm run version
   ```

4. Stage, commit, and push your changes.

5. Manually run the **Publish Hot Fix** GitHub workflow.

   **Note:** This workflow only runs on branches with the `hotfix-releases/` prefix.

   The workflow will:

   * Publish the new patch version.
   * Remove the generated changeset file.

   The workflow requires a `description` input, which is used as part of the workflow run name.
