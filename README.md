# hugo-mondrian-theme

Mondrian-like minimal theme for Hugo static site generator.

![](static/images/screenshot.gif)


# Using

Copy the theme into your `themes/mondrian` folder or add it as a submodule,
```bash
$ git add submodule https://github.com/redraw/hugo-mondrian-theme.git themes/mondrian
$ hugo server -t mondrian
```

Colors are configurable per [content-type](https://gohugo.io/content-management/types/) and you can modify them your `config.toml`, along with minor settings

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

You can test the `exampleSite`
```bash
$ cd themes/mondrian/exampleSite
$ hugo server --themesDir ../..
```

### Notes
[Beerware](https://gitter.im/hugo-mondrian-theme) (?)
