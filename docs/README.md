## Adding Grant Configuration

### Creating a New Grant

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

### Updating an Existing Grant

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
