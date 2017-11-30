# Source for Philippe Grosjean's Web Site

This is the source code created with [blogdown](https://bookdown.org/yihui/blogdown/) for building http://phgrosjean.sciviews.org with [hugo](https://gohugo.io) and hosted in the **phgrosjean.github.io** Github repository (as submodule in the `/public` folder, as explained [here](https://gohugo.io/hosting-and-deployment/hosting-on-github/#host-github-user-or-organization-pages)).

Here are the steps used to create it:

- Install blogdown and hugo (version 0.31.1) in R using `install.packages("blogdown");blogdown::install_hugo()`.

- Create the web site with academic theme using `blogdown::new_site(theme = "gcushen/hugo-academic")` somewhere.

- Create two repositories in Github: `phgrosjean.github.io`and `phgrosjean.github.source`.

- Clone `phgrosjean.github.source` locally and place all the files generated in previous step there, except `/public`. Push to Github.

- Open your terminal in the root directory of this local repository, and make sure the public directory is erased while hugo server is shut down (`rm -rf public`).

- Create a submodule including `phgrosjean.github.io` as `/public` subdirectory within `phgrosjean.github.source` using g`it submodule add -b master git@github.com:phgrosjean/phgrosjean.github.io.git public`.

- Customize `config.toml` and add pages...
