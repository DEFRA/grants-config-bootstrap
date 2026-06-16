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
