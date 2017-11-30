# Source for Philippe Grosjean's Web Site

This is the source code created with [blogdown](https://bookdown.org/yihui/blogdown/) for building http://phgrosjean.sciviews.org with [hugo](https://gohugo.io) and hosted in the **phgrosjean.github.io** Github repository. _The rest of this REAMDE file is mostly a reminder to me about how to set up those sites._

Those two repositories are totally separated, because it is easier for me to commit and push to them separately, i.e., to focus on source, and push to `phgrosjean.github.io` *only* when I am happy with a totally finalized task. I thus followed instructions [here](https://bookdown.org/yihui/blogdown/github-pages.html) to set up those two repositories separately, using `publishDir = "../phgrosjean.github.io"` in `config.toml`.

However, another possibility is to set `phgrosjean.github.io` as submodule in the `/public` folder of `phgrosjean.github.source`, as explained [here](https://gohugo.io/hosting-and-deployment/hosting-on-github/#host-github-user-or-organization-pages)).

Here are the steps used to create this submodule:

- Install blogdown and hugo (version 0.31.1) in R using `install.packages("blogdown");blogdown::install_hugo()`.

- Create the web site with academic theme using `blogdown::new_site(theme = "gcushen/hugo-academic")` somewhere.

- Create two repositories in Github: `phgrosjean.github.io`and `phgrosjean.github.source`.

- Clone `phgrosjean.github.source` locally and place all the files generated in previous step there, except `/public`. Push to Github.

- Open your terminal in the root directory of this local repository, and make sure the public directory is erased while hugo server is shut down (`rm -rf public`).

- Make sure you have an SSH key and the public part is uploaded into your Github account:

```
ssh-keygen -t rsa -b 4096 -C "phgrosjean@sciviews.org"
# Accept default location and generate passphrase
# Add your key into the SSH agent
eval "$(ssh-agent -s)"
ssh-add -K ~/.ssh/id_rsa
# Copy the public part to the clipboard
pbcopy < ~/.ssh/id_rsa.pub
# In your Github account > settings > SSH and PGP keys > New SSH key -> add this key
# Check that you can connect to github
ssh -vT git@github.com # Should not return "Permission denied (publickey)"
```

- Create a submodule including `phgrosjean.github.io` as `/public` subdirectory within `phgrosjean.github.source` using:

```
git submodule add -b master git@github.com:phgrosjean/phgrosjean.github.io.git public
```

- Create `CNAME`, `LICENSE`, `README.md`, `.gitignore`, `.nojekyll` files in `phgrosjean.github.source/static` to be added automatically into `phgrosjean.github.io` when hugo builds the site.

- Make sure that baseurl in `config.toml` is the same as the ur indicated in `CNAME`, ended with `/`.

- Customize `config.toml`, add pages, build the site, push it to github and serve it!
