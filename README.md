Hi! Welcome to the repository for my personal blog / article website that I'm using to post about things I've learnt. Hopefully the knowledge will be useful for others too.

I'll generally be covering topics related to Math or Programming, and maybe some Engineering stuff in there as well.

This site was built on top of the wonderful "ready-to-fork" Reverie Jekyll theme. All blog posts are automatically compiled from Markdown into HTML using Jekyll.

## Reverie Theme

From the creator of Reverie:

> Reverie is a [Jekyll](https://jekyllrb.com/)-powered theme which is simple and opinionated. It's actually a fork of [jekyll-now](https://github.com/barryclark/jekyll-now) with some additional features and personal touches which I've implemented to suit my needs for my blog.

> [Theme demo](https://reverie-jekyll.netlify.app/)

> This is a plug-and-play Jekyll theme best suited to use on [GitHub Pages](https://pages.github.com) (or [Cloudflare Pages](https://pages.cloudflare.com/) if you want to have your repository private) without even setting up a local environment.

### Personal Customizations

I've redone the colors for the webpage to have a nice dark theme. It only requires changing two files:

-   [\_variables.scss](/_sass/_variables.scss)
    -   To define all the colors to use in your custom theme.
-   [style.scss](/assets/style.scss)
    -   Replace all the colors you want to change with references to the ones you defined in [\_variables.scss](/_sass/_variables.scss) using the syntax `$variable_name` in place of the color.
