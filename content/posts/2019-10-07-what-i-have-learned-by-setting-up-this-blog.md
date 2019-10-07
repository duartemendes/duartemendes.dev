+++
title = "Setting up a blog"
date = "2019-10-07"
author = "Duarte Mendes"
cover = ""
tags = ["git submodules", "deno", "toml", "hsts", "whois"]
description = "Things I didn't knew before setting up this blog..."
draft = false
+++

While setting up this blog, I've stumbled upon several things I never heard of.  
Here, I provide a list of those things along with small explanations.

## Git Submodules

The recommended way to add a theme to our Hugo blog is by including the theme as a git submodule.

Git submodules give you the ability to include a git repository as a subdirectory in your own git repository.

Adding a submodule to your repo is as simple as:

```bash
git submodule add https://github.com/panr/hugo-theme-hello-friend.git themes/hello-friend
```

After adding a submodule, you can see that a new file .gitmodules has been created.

```bash
> more .gitmodules

[submodule "themes/hello-friend"]
    path = themes/hello-friend
    url = https://github.com/panr/hugo-theme-hello-friend.git
```

If we peek into the new folder "themes/hello-friend", we'll see that it's a clone of the hello-friend theme repository.

### Cloning a repository with Git Submodules

```bash
git clone --recurse-submodules https://github.com/duartemendes/duartemendes.dev.git
```

### Updating a submodule

```bash
git submodule update --remote themes/hello-friend
```

### Deno is using it

{{< image src="/images/deno_logo_3.svg" style="width: 30%;" >}}

As stated in deno [prerequisites](https://deno.land/manual.html#prerequisites):  
> To ensure reproducible builds, Deno has most of its dependencies in a git submodule.

Check its [gitmodules](https://github.com/denoland/deno/blob/master/.gitmodules) file to find out which submodules it depends on. Typescript is one of them.

Check Git Submodules official [page](https://git-scm.com/book/en/v2/Git-Tools-Submodules) for more information.

## TOML configuration files

[TOML](https://github.com/toml-lang/toml) is a simple configuration file format.

When I first looked at a sample, it reminded me of YAML right away.

You can take a look at this blog's configuration [file](https://github.com/duartemendes/duartemendes.dev/blob/master/config.toml) to see how a TOML configuration file looks.

To be honest, I prefer to look at YAML files rather than TOML ones, as I think YAML is a bit more readable.

## .dev

As you probably have noticed, this blog is being served on a dev domain.

What I find out, was, that both Chrome, Firefox and other browsers force dev top level domains (among others) to use HTTPS.

This is achieved thanks to the HTTPS Strict Transport Security (HSTS) preload list.

This list can contain individual domains, subdomains or even top level domains, in which browsers will automatically enforce HTTPS connections.

You can check a domain status and eligibility or even request for submission in [https://hstspreload.org](https://hstspreload.org).

For more details on this works, go [here](https://security.googleblog.com/2017/09/broadening-hsts-to-secure-more-of-web.html).

## Whois

When buying a domain you're often asked to pay for privacy protection.

What exactly is this that they so much want you to buy? (you might find this for free if you look twice though).

Basically, there is a WHOIS database that contains all the registered domains and their information.

You, or anyone with internet access, can query for domains this database in [https://www.whois.com/whois](https://www.whois.com/whois).

When searching for a domain, you'll see lots of data, like registrant, admin, tech and billing details.

If you don't opt in for the privacy protection, your data, like your name, email and address will appear here, available to anyone.

If you do, data will be masked with things like "REDACTED FOR PRIVACY".

So, be sure to not contribute to your digital footprint :)

## Wrapping up

These are the things that I came across while setting up this blog. Writing about it, made me research more about it, learning even more.

Sharing is indeed learning. Take care :)
