# 8bitmixtape.github.io/NeoDocs

GitBook documentation for the [8Bit-Mixtape-Neo](https://github.com/8BitMixtape/8Bit-Mixtape-NEO) project.

# Publishing

Any changes made to the documentation will automatically get published to [8bitmixtape.github.io/NeoDocs](https://8bitmixtape.github.io/NeoDocs) 
via Travis CI once the changes are merged into the `source` branch.

# Requirements

* npm

# Preparation

First, install GitBook's CLI with the following commands:

1. `npm install`
2. `npm run docs:prepare`

# Development

A local development server can be started with `npm run docs:watch`. This server
will watch for local changes and reflect them in the build directory. The
development server also hosts the website at `localhost:4000`.

Alternatively, a static site can be built by running `npm run docs:build`.

# Branch Explanation

This repo has a slightly unconventional branching setup.  This is leftover from when 
it was hosted on GitHub Pages:

> Most GitHub Pages-based repos tend to use `master` for the source, and `gh-pages` for the rendered
> website. Because this repo is intended to host an organization webpage, then per
> [GitHub's requirements](https://help.github.com/articles/user-organization-and-project-pages/)
> the rendered website MUST appear on the `master` branch. Since the `master`
> branch can no longer be used to hold the source, a separate branch must be made
> for that, which in this case is called `source`.


## How was this set up?

* Clone repo
* Run `npm install`
* Go to **Repository settings**, make sure *GitHub pages* are enabled, and select the `gh-pages` branch
* You should be able to access your repo using the address displayed by GitHub (something like `[yourusername].github.io/[repositoryname]`)
* Enable this repository in Travis, from [your Travis dashboard](https://travis-ci.org/profile). If you don't have one, you'll have to create an account there. If you do, you might need to *Sync account*, so the repository shows up in the list. Then flick the switch on!
* Generate and set up deploy keys for the repository (run these commands when inside the repo folder):
  * `ssh-keygen -f id_rsa -t rsa -C "your_email@example.com"` (when asked, leave the passphrase empty).
  * Add the contents of `id_rsa.pub` as a deploy key for your Github repository: in `https://github.com/<your name>/<your repo>/settings/keys` - make sure to allow 'write' access or Travis won't be able to push
  * Install Travis CLI client: `gem install travis`
  * Log into the CLI and encrypt the private key you generated, `id_rsa`:
    * `travis login`
    * `travis encrypt-file id_rsa --add` (will add the decrypt command to recreate `id_rsa` in the current folder as a `before_install` script in `.travis.yml`)
  * Delete `id_rsa` and `id_rsa.pub`: `rm id_rsa id_rsa.pub`
  * Add `id_rsa.enc` to git and commit: `git add id_rsa.enc; git commit -m 'add encrypted key'`
* Make sure the values in the `env` section in `.travis.yml` are correct, update where necessary

That should be it!

If you push a commit to GitHub and Travis runs the script successfully and a new version is published on the `gh-pages` branch, looks like you're in a good position to enable Travis' `Cron` from the project settings in Travis. And then the process will be run automatically for you.

**Note** that if you revoke the deploy key in GitHub, then Travis won't be able to push to the repo. You'll need to generate a new one again, encrypt it with the Travis client, and update, commit and publish the `id_rsa.enc` file.

**Also note** that we are copying the `CNAME` file to the `output` folder before publishing because we use a custom domain and for some obscure reason GitHub keeps forgetting it (or resetting it to blank) if the domain is not set in the repository's `gh-pages` branch.