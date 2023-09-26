## Description
This Repository provides instructions for setting and publishing your private LogSeq Graph as a shared site <owner>.github.io location using a GitHub Action.
It also includes information about setting up the required API key and adding an index.html file for easy navigation.

exmple:
> If the /<owner/> `BestOwner` builds a privat repo `LogBook` containing a graph then this action would publish it under `bestowner.github.io/LogBook`


## How does it work
When information is pushed into the Private LogSeq repository containing the the Graph, an action will trigger and convert all [public pages](https://docs.logseq.com/#/page/publishing%20(desktop%20app%20only)?anchor=ls-block-650b2586-475f-42d2-9473-5553f6901713) in the graph onto you public website.


# Setup
## Configure LogSeq client to use a Github Repository
To set up your LogSeq Graph in Githup use the 


## Configure your public Repository
This Repository will be hosting all the graphs as websites `<owner>.github.io`

1. ### Create a site
    Follow these [instruction](https://docs.github.com/en/pages/quickstart) on how to build your own .github.io website if you dont allready have one.
2. ### Set up an access Token
    The Logseq Graph Repositores will reeuier an access token in order to publish to this site
  -  I suggest using the new [Fine-grained Tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
  but classic will work as well since you will only by suplying to a privat repository.
3. ### Set up an Index
  Every Graph will publish udner a differnet subfolder so if you brows directly into the site you will recive an `404 error`
  to fix this you can copy the github.io/index.html int to the root of your new `<owner>.github.io` site.

  *This is very simple index file that can be easly replaced with somthing better or tweaked for your personal use.*

## Configure Github Repository to publish the site on <owner>.github.io
This uses the [logseq/publish-spa](https://github.com/logseq/publish-spa) solution to convert the Graph into a website using a different action to modify the resault. 

### Github Action
To publish your LogSeq Graph in a remote repository, you need to provide the GitHub Action with an API key called 'GH_TOKEN'. 

1. To create the 'GH_TOKEN' secret in the '<owner>.github.io' repository, under "`Settings`>`Secrets and variables`>`Action`>`Secrets`" (/settings/secrets/actions).
Name the secret GH_TOKEN and add the API key as its value.

2. Copy the file workflows/logseq-publisher.yaml to you new LogSew Repository under the folder '.github/workflows/' to your graph's github repository.

### Destination Change
you can manuly set change the destination by adding the following variables under "`Settings`>`Secrets and variables`>`Actionv>`Variables`" (/settings/variables/actions).
`FOLDER`
`GITHUB_IO`

example: 
> FOLDER = LogGraph
> GITHUB_IO = NextBestOwner
> resaults in: 'nextbestowner.github.io/LogGraph'





## Configure <owner>.github.io to list out all publishesd Graphs







### Index
Since each Graph has its own subfolder, there is no basic index file for the site. Browsing directly into a subfolder will result in a 404 error. However, accessing newowner.github.io/LogSeq will work.

To provide easy navigation, I have included an index.html file that can be placed in the root of newowner.github.io. This file dynamically lists all the subfolders as buttons for accessing the graphs.

You need to replce <NewOwner/newowner.github.io> in fetch('https://api.github.com/repos/<NewOwner/newowner.github.io>/contents/') for this to work.
