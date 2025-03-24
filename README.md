# Common Theme Template

## What is it?

This is a template repo for CYF curriculum developers to build new curricula sites, using Common theme. Each person, team, or org builds its own Hugo site that uses the common theme and content modules, and then makes any customisations they need and deploys it wherever they want.

The documentation is here => https://common.codeyourfuture.io/

The theme is here => https://github.com/CodeYourFuture/curriculum and there's more extensive READMES in the subdirectories.

## Examples

https://curriculum.codeyourfuture.io/
https://workshops.codeyourfuture.io/
https://curriculum.migracode.org/

## Quickstart Mac

### Clone the repo

1. Choose [Use this template](https://github.com/new?template_name=CYF-Common-Theme-Template&template_owner=CodeYourFuture) to create a new repo with this template.
1. Clone your new repo to your local machine and `cd` into it.

### Set up Auth and config

1. Rename `.env.example` to `.env`
1. Go to https://github.com/settings/personal-access-tokens/new
1. Create a new token, choosing `Public Repositories (read-only)` `0 Permissions` and add it to your `.env` as the value for `HUGO_CURRICULUM_GITHUB_BEARER_TOKEN`.
1. Run `brew install go hugo` to install Go and Hugo globally
1. Now, init your new site as a Hugo module:

```zsh
  hugo mod init github.com/$ORG/$REPO/$DIR
```

6. Add your modules in `hugo.toml`

### Local development

1. In the /template folder, run `npm install` to install the dependencies.
1. Run `npm run start:dev` to start the development server.
1. Open your browser to `http://localhost:1313/` to see your site.

🎉

## Look and feel

To customise the css, make a dir `assets/custom-theme` and throw any scss in there. It will be compiled and added last. To change site logo/s, make a dir and add svgs to `assets/custom-images/site-logo/`. They will be added to the site header. Framework is here => https://github.com/CodeYourFuture/curriculum/tree/main/common-theme/assets/styles

## Site structure, pages, etc

https://common.codeyourfuture.io/common-theme/pages/
https://common.codeyourfuture.io/common-theme/block-types/

Use the included `create_module.sh` script to generate blank module structures, filled with useful hints and tips.

Add your content to `content/` and customise the site config in `config.toml`. Please contribute any improvements you make back to the common theme and content modules.

## Useful tips

### You really do need the token

> ERROR 🏷️ Site needs a GITHUB_BEARER_TOKEN. Check the README

This platform has tight integration with Github APIs, so you can connect repos, pull in readmes, issues and PRs. To make this work you NEED a bearer token from Github. Go look in the curriculum READMEs for more details if the quickstart guide is not clear enough.

https://github.com/CodeYourFuture/curriculum

### Adding modules and making local changes

https://gohugo.io/hugo-modules/configuration/

For each module you import, add a `replace` directive to your `go.mod` file - if you forget to do this, you won't get live updates to your site when shared content changes. CI will remind you if you forget.

### Vendoring

If you want to _see_ the files you just mounted into your virtual filesystem, run `hugo mod vendor` to copy the files into your site. This is useful for debugging and clarity, but not necessary for development.
