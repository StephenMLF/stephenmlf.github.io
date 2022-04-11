---
layout: post
title:  "Test Setup"
date:   2022-04-11 09:00:00 +0100
categories: evolver
---


# Test Setup

### AM Update:

Supporting Nils with getting Evolver set up in the studio for tests later this week. Took a little minute to get set up myself after being on annual leave last week.

We immediately hit

<pre class="special" style="color: darkred!important">
  ▄████  ██▓▄▄▄█████▓    ██░ ██ ▓█████  ██▓     ██▓    
 ██▒ ▀█▒▓██▒▓  ██▒ ▓▒   ▓██░ ██▒▓█   ▀ ▓██▒    ▓██▒    
▒██░▄▄▄░▒██▒▒ ▓██░ ▒░   ▒██▀▀██░▒███   ▒██░    ▒██░    
░▓█  ██▓░██░░ ▓██▓ ░    ░▓█ ░██ ▒▓█  ▄ ▒██░    ▒██░    
░▒▓███▀▒░██░  ▒██▒ ░    ░▓█▒░██▓░▒████▒░██████▒░██████▒
 ░▒   ▒ ░▓    ▒ ░░       ▒ ░░▒░▒░░ ▒░ ░░ ▒░▓  ░░ ▒░▓  ░
  ░   ░  ▒ ░    ░        ▒ ░▒░ ░ ░ ░  ░░ ░ ▒  ░░ ░ ▒  ░
░ ░   ░  ▒ ░  ░          ░  ░░ ░   ░     ░ ░     ░ ░   
      ░  ░               ░  ░  ░   ░  ░    ░  ░    ░  ░
</pre>

Eventually resolved by running:

<pre><code>git lfs migrate import --no-rewrite mlf_sdk_package/MLFSDK.dylib
 </code></pre>

from an answer [here](https://stackoverflow.com/questions/56016033/adding-missing-lfs-files-that-causes-encountered-x-files-that-should-have-bee) since it appeared that the `.dylib` was supposed to be a pointer (on LFS) but wasn't - as if it had been committed from a computer that didn't have `git lfs` installed.

Got things up and running on my end (remote working in Poland on an underpowered laptop, so hopefully won't need to run the main patch too often), and will see if other issues arise that need taking care of when running `develop` of all repos.

