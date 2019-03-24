# hugo-mondrian-theme

Mondrian-like minimal theme for Hugo static site generator.

![](https://raw.githubusercontent.com/redraw/hugo-mondrian-theme/master/images/screenshot.gif)


# Using

Copy the theme in `themes/mondrian` folder or add it as a git submodule,
```bash
$ git submodule add https://github.com/redraw/hugo-mondrian-theme.git themes/mondrian
$ hugo server -t mondrian
```

Colors are configurable per [content-type](https://gohugo.io/content-management/types/) and you can modify them in your `config.toml`, along with minor settings

```toml
[params]
  showHeader = true
  showTags = true
  debug = false
  [params.colors]
    post = "orangered"
    page = "gold"
    sketch = "limegreen"
```

If you want to test the `exampleSite`, run
```bash
$ cd themes/mondrian/exampleSite
$ hugo server --themesDir ../..
```

### Notes
[Beerware](https://gitter.im/hugo-mondrian-theme) (?)
