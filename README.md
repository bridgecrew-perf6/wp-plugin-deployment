# Deploying a WordPress Plugin from GitHub to SVN

This script allows for automated deployments of plugins in GitHub repos to the WordPress Plugin Repository.

This does not have to be automated with the script, and instructions for managing plugins that way will be added to the wiki.

## Prerequisites

- Add an `.svnignore` file to the root of the project.

  - Check with the Plugin Repository structure to see which files are currently being excluded. Make sure those files/directories are listed in your `.svnignore`.
  - This is commonly used to exclude build-time dependencies. i.e. `webpack.config.js`, `gulpfile.js`, etc.

- Clone this repository and move the `deploy.sh` script into the root of your `plugins` directory.

  - For example, if your plugins directory is named `plugins`:

    ```bash
    └── plugins
        ├── deploy.sh # this is our script
        ├── plugin-folder
        ├── another-plugin-folder
        └── etc.
    ```

## Instructions

1. Make any necessary changes to your plugin and deploy to the main/master branch

2. Tag a release.

   - This tag number should be the same as the new revision of the plugin on the Plugin Repository.
   - This can be done on the command line or through GitHub itself

3. Navigate to your plugins directory and run the `deploy.sh` script

   ```bash
   cd plugins && ./deploy.sh
   ```

   It will ask you a series of questions:

   1. **Plugin Slug** - This is the slug on the WordPress Plugin Repository
   2. **Plugin Directory** - Name of the folder on your drive holding the plugin's git repository
   3. **SVN Assets Directory** - The folder in your plugin's git repository that holds the assets
   4. **Main Plugin File** - The main plugin file to be included initially
   5. **Temp Directory Location** - Leave this as the default unless you have permissions errors
   6. **Remote SVN Repo** - This is the full url of the plugin in the WordPress Plugin Repository
   7. **WordPress SVN Username** - This is the username you use to log on to wordpress.org

## Credits

[Original Script](https://github.com/GaryJones/wordpress-plugin-svn-deploy) by GaryJones
