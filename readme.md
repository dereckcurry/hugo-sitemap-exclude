# A Template That Allows For Pages To Be Excluded From The Sitemap.xml File In Hugo

If you don't want some of your pages to be included in the **sitemap.xml** file on your Hugo website, this template may be what you are looking for.

These template is designed to work with Hugo versions 0.54.x and 0.55.x. It will likely work with other versions, but has not been tested.

The [default Hugo template](https://github.com/gohugoio/hugo/blob/release-0.55.2/tpl/tplimpl/embedded/templates/_default/sitemap.xml) for the **sitemap.xml** file includes all pages by default in the sitemap used by search engines to index your site. Unfortunately, there may be times when you wish to have a hidden page on your site and therefore you wouldn't want the page to show up in the **sitemap.xml** file. This template gives you more control of the **sitemap.xml** file contents by allowing you to explicitly state in the page front matter if you wish to have the page excluded. In absense of a specifically defined exclusion values, the template includes the page in the **sitemap.xml** file.


## Template Installation

To use this new template, you will first need to install this new **sitemap.xml** template in your **/layouts/_default/** directory.

```
root
    layouts
        _default
            sitemap.xml
```

If for some reason your theme has moved the **sitemap.xml** template to a different directory, then you'll probably need to install this new template in the corresponding directory structure that follows that of your theme.


## How To Use

After installing, the new **sitemap.xml** template should be used when compiling/generating your site.

To take advantage of the flexibility of this new template, you'll need to make changes in the front matter of each page you wish to exclude from the sitemap. This is accomplished by placing **sitemapExclude = true** in the page's front matter. I'm using TOML for my front matter, so you may need to modify the syntax to confirm to the configuration syntax used in your front matter.

```
+++
title = "Excluded Page"
sitemapExclude = true
+++
```

To exclude a page, the **sitemapExclude** param value has to be set to **true**. Not including the **sitemapExclude** param, or setting the value to something other than **true**, will have the page included in the **sitemap.xml** file.

That's it. When the site is generated/compiled, the page should be excluded from the **sitemap.xml** file.

As always, test locally before deploying your site to production.


## Caveat

When excluding a page, a blank line is inserted in the **sitemap.xml** file. Technically this is some data leakage as it would indicate that you excluded a page. It would not indicate which page is excluded, just that somewhere on your site you excluded a page. Probably not a big deal to most sites, but just be aware of this.


## Conclusion

I'm new to Hugo, so forgive me if I didn't follow conventions correctly. Please let me know if I did something wrong.

I've tested this template locally and with my personal [site](https://dereckcurry.com) and haven't found any issues. But please let me know if you discover any problems.

You can find a more detailed writeup about this template on my [blog](https://dereckcurry.com/posts/excluding-pages-from-the-sitemap/).