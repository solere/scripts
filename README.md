# scripts
place to share scripts regarding working with github

external requirements : 

the json cli parser "jq" is used, to obtain jq either check out the source on github :

https://github.com/stedolan/jq/wiki/Cookbook

or if you are on CentOS, RH, Fedora -- you can pull it from the epel repository - something like : 

# install the epel yum repo config
yum install -y epel-release

# cache the repos contents ( not really required )
yum makecache

# install jq - which will be at /usr/bin/jq
yum install -y jq.x86-64

-- pretty much everything else is in bash

to connect with github.com, you will need an access token, put that token into 
keys/ORG.key where ORG is the github.com organization level 

We're also going to prepare a gist per PR that we check, so make sure the token
has access to making a gist, also.

bin/openPRs 
--
oddly specific bash script to seek out state="open" pull requests on an ORG/repo 
combination to then pull that repo and checkout the pre-merged tree via the merge sha.

It's a nice way to see if the merged code will compile in advance, when there's a 
firewall between the github.com repo and your CI instance; the intent is to PULL
the open PRs periodically.

