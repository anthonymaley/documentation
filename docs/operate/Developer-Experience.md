---
layout: default
title: Developer Setup
nav_order: 601
parent: Operate
has_children: false
---
# Developer Experience

## Local environment

In this section you will find basic information which help you to configure your local environment.

### Assumptions

At this step you should already have:

- Installed Vouch application on your mobile device ([Vouch App](https://play.google.com/apps/testing/io.vouch.Vouch.dogfood))
- Access to Vouch Slack ([Vouch Slack](https://ledgrinc.slack.com))
- Access to AWS Console [AWS](https://ledgrinc.auth0.com/samlp/1BMM3I2bBoL71hT0J7wrjWXhUU3xdocB?connection=vouch-zero-password)
- Access to Vouch email via the Google GSuite (firstname.lastname@vouch.io)

### Install clojure

Almost all projects require Clojure to be installed. You also need Java as Clojure dependency.

[Install Clojure](https://clojure.org/guides/getting_started)

Verify working Clojure on your machine by running `clojure` command.

### AWS Credentials

To have access to AWS resources you need to have `~/.aws/credentials` file with the content:

```
[vouch]
aws_access_key_id=PASTE_HERE
aws_secret_access_key=PASTE_HERE
```

Notice that profile name must be exactly `vouch`.

[Login to AWS](https://ledgrinc.auth0.com/samlp/1BMM3I2bBoL71hT0J7wrjWXhUU3xdocB?connection=vouch-zero-password)

[Get AWS Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html#id_users_create_console)

(TODO establish exact permission that we need to provide, to avoid granting `Administrator` access)

### GitHub SSH auth

Setup SSH authentication on GitHub.

[Add SSH key to GitHub](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)

If you don't have your SSH public/private key pair, you need to [generate new one](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

Now enable SSO on your key in GitHub for Vouch company.

[Enable SSO on GitHub](https://docs.github.com/en/github/authenticating-to-github/authorizing-an-ssh-key-for-use-with-saml-single-sign-on)

After that, `ssh-agent` must be active in your system in order to download private dependencies during modules start.

Run:

```
eval `ssh-agent`
ssh-add
```

To make it persistent, add to your `~/.bash_profile` file lines:

```
eval `ssh-agent` &> /dev/null
ssh-add &> /dev/null
```

### Docker registry auth

Setup docker registry authentication in order to download private docker images from GitHub

First [Create GitHub Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

Token must have at least `read:packages` permission.

Enable SSO for that token for Vouch company, the same as on <strong>GitHub SSH auth</strong>

Run:

```
docker login docker.pkg.github.com
```

and provide your GitHub `username` and personal access token (as a `password`).

### Maven repository auth

To have access to private Maven repositories, create `~/.m2/settings.xml` file (or modify according to below content):

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      https://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>my.datomic.com</id>
            <username>ops@vouch.io</username>
            <password>M2_PASSWORD</password>
        </server>
        <server>
            <id>github-vouchio-abci-protobuf</id>
            <username>GITHUB_USERNAME</username>
            <password>GITHUB_PERSONAL_TOKEN</password>
        </server>
    </servers>
</settings>
```

Replace `GITHUB_USERNAME` and `GITHUB_PERSONAL_TOKEN` with your credentials.

To get `M2_PASSWORD` use AWS CLI command:

```
AWS_PROFILE=vouch AWS_REGION=us-east-1 aws ssm get-parameter --name /local-dev/my.datomic.com/password --with-decryption
```

or if you don't have AWS CLI, login into AWS and go to SSM section, find parameter
[/local-dev/my.datomic.com/password](https://console.aws.amazon.com/systems-manager/parameters/local-dev/M2_PASSWORD/description?region=us-east-1&tab=Table)
and copy its value

### Running REPL

This tutorial is prepared for Intellij IDEA 2020.

#### Open Intellij IDEA

#### Install Cursive plugin

```{r 8.1.7.2, echo=FALSE, fig.retina=3, fig.cap="Download Cursive", fig.align = 'center', out.width = '100%'}
knitr::include_graphics("Developer/Cursive.png")
```

#### Clone Clojure project using SSH (for example [digital-key-api](https://github.com/vouchio/digital-key-api))

#### Open it as a new project using IDEA

#### Go to Cojure Deps section and make sure you can refresh Deps

```{r 8.1.7.5, echo=FALSE, fig.retina=3, fig.cap="Check Deps configuration", fig.align = 'center', out.width = '50%'}
knitr::include_graphics("Developer/Deps.png")
```

if you see an error:
```
Error building classpath. connector is not available:
com.jcraft.jsch.agentproxy.AgentProxyException: connector is not available:
        at com.jcraft.jsch.agentproxy.ConnectorFactory.createConnector(ConnectorFactory.java:120)
```
make sure you've run:
```
eval `ssh-agent`
ssh-add
```
in context of running IDEA

#### Add new REPL configuration

Follow the steps on screenshot

```{r 8.1.7.6, echo=FALSE, fig.retina=3, fig.cap="Add REPL task", fig.align = 'center', out.width = '100%'}
knitr::include_graphics("Developer/Add-Task.png")
```

`*` form the screenshoot - If you run `cljs` projects you need to select `clojure.main` option.

#### Run new task (default: Shift + F10)

#### You should be able to run tests interactively

Default abbreviation - `Ctrl + Shift + A` type "REPL run" and select proper action

### Git commit signing

All code must be signed using your GPG key. [How-To set it up docs on Github](https://docs.github.com/en/github/authenticating-to-github/signing-commits)

When you want to sign your commits with your vouch.io email address, [make sure you associate the email address with your GPG key](https://docs.github.com/en/github/authenticating-to-github/associating-an-email-with-your-gpg-key).

To automatically sign commits with your vouch.io address,

- move all your vouch code repositories to a specific directory (in the example `~/code/vouch/`)
- setup the following in `~/.gitconfig`

```
[includeIf "gitdir:~/code/vouch/"]
        path = ~/code/vouch/.gitconfig
```

And in `~/code/vouch/.gitconfig`

```
[user]
        email = stijn.opheide@vouch.io
[commit]
        gpgsign = true
```
