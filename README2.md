# Description

This repository provides instructions for setting up and publishing your private LogSeq Graph as a shared site \<owner\>.github.io location using GitHub Actions.

For example:
> If the \<owner\> `BestOwner` builds a private repository `LogBook` containing a graph, then this action would publish it under `bestowner.github.io/LogBook`.

## How does it work

When information is pushed into the private repository containing the LogSeq graph, an action will trigger and convert all [public pages](https://docs.logseq.com/#/page/publishing%20(desktop%20app%20only)?anchor=ls-block-650b2586-475f-42d2-9473-5553f6901713) onto your public website under a subfolder.



# Setup

## Configure LogSeq client to use a GitHub
To set up your LogSeq Graph in GitHub, you need to use [Logseq-Git-Sync-101](https://github.com/CharlesChiuGit/Logseq-Git-Sync-101)

Detailed instruction on how to do this can be found at [Good and Geeky](https://www.youtube.com/watch?v=c2HrdSOoVD8&t=1s)

## Configure your public Repository (website)

This repository will be hosting all the graphs as websites `<owner>.github.io`.

1. ### Create a site

    Follow these [instructions](https://docs.github.com/en/pages/quickstart) on how to build your own .github.io website if you don't already have one.

2. ### Create an access Token

    The LogSeq Graph Repositories will require an access token in order to publish to this site. I suggest using the new [Fine-grained Tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens), but the classic tokens will work as well since you will only be supplying them to a private repository.
3. ### Set up an Index
    Since each graph has its own subfolder, there is no basic index file for the site. Browsing directly into a subfolder will result in a 404 error. However, accessing `newowner.github.io/LogSeq` will work.

    To provide easy navigation, I have included an `index.html` file that can be placed in the root of `newowner.github.io`. This file dynamically lists all the subfolders as buttons for accessing the graphs.

    Simply copy the `github.io/index.html` file into the root of your new `<owner>.github.io` site.

    *This is a very simple index file that can be easily replaced with something better or tweaked for your personal use.*


## Configure your privae Repositories (graphs)

The Graph repositories use the [logseq/publish-spa](https://github.com/logseq/publish-spa) solution to convert the Graph into a website using a modified action.

1. ### Set up Token Authentication
Before you can publish your LogSeq Graph in a remote repository, you need to provide the GitHub Action with an API secert called 'GH_TOKEN'.
- To create the 'GH_TOKEN', go to "`Settings` > `Secrets and variables` > `Action` > `Secrets`" (/settings/secrets/actions). 
- Name the secret GH_TOKEN and add the API access token created in **step 2**.

1. ### Create GitHub Action
Copy the file `workflows/logseq-publisher.yaml` to your new LogSeq repository under the folder `.github/workflows/` in your graph's GitHub repository.

3. ### Destination Change (optional)
You can manually change the destination by adding the following variables under "`Settings` > `Secrets and variables` > `Action` > `Variables`" (/settings/variables/actions).
- `FOLDER`
- `GITHUB_IO`

For example:
> FOLDER = LogGraph
> GITHUB_IO = NextBestOwner
> results in: 'nextbestowner.github.io/LogGraph'


