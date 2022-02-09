# Wordpress with composer

This folder contains recommended starter configuration for a composer-managed Wordpress project on Pantheon hosting utilizing an external Git provider, a Continuous Integration service, and a [Pull Request workflow](https://pantheon.io/docs/guides/build-tools/pr-workflow). The tooling and templates provided enable developers to quickly generate a new project implementing common best practices and automation to build, test, deploy, and update a Wordpress project.

Note that this configuration *is not compatible* with Pantheon's [Integrated Composer](https://pantheon.io/docs/integrated-composer) workflow for managing package and dependency updates in the Pantheon site dashboard.

## Create a new project with this configuration

If you are using the [Terminus Build Tools Plugin](https://pantheon.io/docs/guides/build-tools) to scaffold your Pantheon project via the `terminus build:project:create` command, you can specify the `--ci-template` option to use the recommendations provided in this repo on your project. For example:

```
terminus build:project:create --ci-template="git@github.com:lcatlett/tbt-ci-templates.git" --git=github --team='My Organization Name' d9 my-site

```

See the [Build Tools documentation](https://github.com/pantheon-systems/terminus-build-tools-plugin/blob/3.x/README.md#command-options) for a more detailed overview of the options available for customization in `build:project:create` and other terminus commands provided by the plugin.

To use these templates on an existing project without the use of Terminus Build Tools, you should copy the `.ci` folder to your project root and the corresponding folder under the providers folder also to your project root. Then, follow the instructions in the relevant section below.

## CircleCI

If you need to enable CircleCI for an existing project, after copying files you should add the following environment variables to CircleCI configuration:

- ADMIN_EMAIL
- ADMIN_PASSWORD
- ADMIN_USERNAME
- TERMINUS_TOKEN
- TERMINUS_SITE
- GITHUB_TOKEN
- GIT_EMAIL
- TEST_SITE_NAME

Also, a ssh private key should be added to the project configuration and the corresponding public key should be added to a Pantheon account with enough permissions over the site.

## Gitlab CI

If you need to enable GitlabCI for an existing project, after copying files you should add the following environment variables to GitlabCI configuration:

- ADMIN_EMAIL
- ADMIN_PASSWORD
- ADMIN_USERNAME
- TERMINUS_TOKEN
- TERMINUS_SITE
- GITLAB_TOKEN
- GIT_EMAIL
- TEST_SITE_NAME
- SSH_PRIVATE_KEY
- TERMINUS_BUILD_TOOLS_PROVIDER_GIT_GITLAB_URL

The TERMINUS_BUILD_TOOLS_PROVIDER_GIT_GITLAB_URL value will be "gitlab.com" or your gitlab instance domain.

## Bitbucket Pipelines

If you need to enable Bitbucket Pipelines for an existing project, after copying files you should add the following environment variables to Bitbucket Pipelines configuration:

- ADMIN_EMAIL
- ADMIN_PASSWORD
- ADMIN_USERNAME
- TERMINUS_TOKEN
- TERMINUS_SITE
- BITBUCKET_USER
- BITBUCKET_PASS
- BITBUCKET_AUTH
- GIT_EMAIL
- TEST_SITE_NAME
- COMPOSER_AUTH
- SSH_PRIVATE_KEY

## Github Actions

If you need to enable Github Actions for an existing project, after copying files you should add the following secrets to Github Actions configuration:

- ADMIN_EMAIL
- ADMIN_PASSWORD
- ADMIN_USERNAME
- TERMINUS_TOKEN
- TERMINUS_SITE
- SSH_PRIVATE_KEY
- GH_TOKEN
