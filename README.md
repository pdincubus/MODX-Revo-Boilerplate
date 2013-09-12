#MODX Revolution Boilerplate basics

A bunch of stuff to quickly get some sensible basics into a new [MODX Revolution](http://modx.com/) install. There's a folder for each type of resource. Simply make a new resource of that particular type and copy in the code.

Now available on the MODX Extras repo!

[MODX-Revo-Boilerplate](http://modx.com/extras/package/modxrevoboilerplate)

[MODX-Revo-Boilerplate-With-Subpackages](http://modx.com/extras/package/modxrevoboilerplatewithsubpackages)

##Templates

###Default

Used by default in MODX, very basic HTML structure. Pulls in a head, foot and aside chunk.

###Article & ArticleContainer

For sites using Articles, you'll definitely want new templates for the layout in that section. These two templates have sane defaults and ensures all repeated code is pulled out into head, foot & articleSidebar chunks.


##Assets

Assets should usually be put in /assets/templates/{TEMPLATEFOLDERNAME}, e.g:

* CSS: /assets/templates/{TEMPLATEFOLDERNAME}/css
* LESS: /assets/templates/{TEMPLATEFOLDERNAME}/less
* All javascript libraries, jQuery, Modernizr, etc: /assets/templates/{TEMPLATEFOLDERNAME}/js/lib
* All your custom js files: /assets/templates/{TEMPLATEFOLDERNAME}/js
* All images related to your template layout: /assets/templates/{TEMPLATEFOLDERNAME}/img
* etc.

The templates and chunks in this repository assume you've put these files in the same place. If not, make sure you update the relevant paths. The assets are bundled with the transport package, and put in /assets/templates/default

###CSS

I use LESS just about all the time.

Includes the HTML5 Boilerplate normalise CSS (with a few tweaks), Internet Explorer HTC behaviour file for border-box box-sizing method and background-size, clearfixes, classes, and basic print styles.

###js

Includes Modernizr for YepNope and making people think that old versions of Internet Explorer are futuristic. Kind of. Also includes local version jQuery for fallback should the CDN download fail, and jQuery Easing for nicer animations.

Selectivizr is also in there for those who want its functionality to support older versions of *cough* Internet Explorer.

I've also put a couple of extras in the js/lib/plugins.js file - [DarthPhader](https://github.com/pdincubus/jquery.DarthPhader), [Shlider](https://github.com/pdincubus/jquery.Shlider) and [ShliderWay](https://github.com/pdincubus/jquery.ShliderWay) because I use them a lot.


##Chunks

###site.head and site.foot

Beginning and end of the templates. I've added two placeholders - [[+bodyClass]] and [[+template]].

[[+bodyClass]] is useful for complex sites and when passed into the [[$head]] will add that class name to the body tag. Can help save a bunch of extra templates (sometimes).

[[+template]] help make your [[$site.head]] & [[$site.foot]] more generic and easier to chuck into a new site without messing too much. See the BaseTemplate template for how to use.

###site.aside-standard

Chuck everything in here that you would have in your aside.

###articles.aside

Contains most things that were pulled out of the stock Articles templates but are repeated on both container and article template. Nicely wrapped in an aside

###fi.contact-email and fi.contact-form

Install the FormIt extra, and with these two simple chunks you can easily drop a working contact form on any page with little to no customisation required.

###wf.row

Wayfinder's default setup for outputting a menu item needs a bit of tweaking since we've used the link_attributes to apply a class to the body tag.

###quip.comment, quip.add-comment, articles.latest-post-tpl, articles.archive-group-by-year, articles.article-row-tpl, articles.archive-row

Replacement, lovely and trimmed down version of the standard Quip chunk


##Snippets

###copyYears

Works out the copyright for the footer.

###currentUrl

Clue is in the name

###formatSearchUrl

Some preformatting for passing to the SimpleSearch on the Page Not Found error page.


##Content Pages

###Page Not Found

Requires SimpleSearch extra, formatSearchUrl and currentUrl snippets. Does a lookup for what page you tried to access and shows results in a list (if any).

###robots.txt

Disallows access to a bunch of MODX folders to SpiderBotMonkeys. Also points out the URL of the sitemap (edit this to your URL). You'll need to install the GoogleSiteMap extra to make the sitemap.xml file

###humans.txt

You can pretty much do what you want in this file, but point out developer, designer, technology used, etc.

###Search Results Page

Clue is in the name really!


##Extras

I generally use the following extras most of the time:

* [Articles](http://rtfm.modx.com/extras/revo/articles). This in turn installs a load of extras it needs. Useful for simple blogs.
* [CodeMirror](http://modx.com/extras/package/codemirror). Syntax highlighting and stuff for anything that isn't a standard content page.
* [Google Analytics Dashboard Widget](http://modx.com/extras/package/googleanalyticsdashboardwidget) - graphs and pretty things on your dashboard
* [FormIt](http://rtfm.modx.com/extras/revo/formit). For form sending/validation, etc
* [Gallery](http://modx.com/extras/package/gallery). Pictures. Grouped. Like in a gallery.
* [getRelated](http://rtfm.modx.com/extras/revo/getrelated). Goes and sees if it can find content related to the page you're on. Useful in Articles pages.
* [getResources](http://rtfm.modx.com/extras/revo/getresources). Useful for all kinds of things.
* [GoogleSiteMap](http://rtfm.modx.com/extras/revo/googlesitemap). Generates XML sitemaps for Spiders, etc
* [JSONDerulo](http://modx.com/extras/package/jsonderulo). Pulls in and outputs JSON feeds for common social feeds.
* [phpThumbsUp](http://modx.com/extras/package/phpthumbsup). Alternative to phpThumbof or pThumb. Does not hold up page load times like either of those. More config required, but performs well... or...
* [pThumb](https://github.com/oo12/phpThumbOf). Crop, thumbnail and alter images automagically. Offers improvements over the original phpThumbOf.
* [setPlaceholders](https://github.com/oo12/setPlaceholders/). Performs a combination of features from [getResourceField](http://modx.com/extras/package/getresourcefield), [UltimateParent](http://modx.com/extras/package/ultimateparent) and others. Really flexible package and well documented!
* [SimpleSearch](http://rtfm.modx.com/extras/revo/simplesearch). For use on the Page Not Found error page.
* [TinyMCE](http://modx.com/extras/package/tinymce). Pretty much the only choice you have for a reasonable text editor in MODX Revo. There is a CKEditor extra but the last time I tried it out it didn't have internal link integration like TinyMCE does. Shame because it's a much nicer RTE.
* [VersionX](https://github.com/Mark-H/VersionX2). Content / chunk version tracker extra. Useful for rolling back to a previous version of something.
* [Wayfinder](http://rtfm.modx.com/extras/revo/wayfinder). Makes menus easy. These can also be done with getResources!


##Transport Package

This is *not* *fully* *tested*. Be careful, the sky may fall down.

* If you *only* want the snippets, chunks, assets and templates - use the default package.
* If you want the *full* package - install the "subpackages" transport package. This includes many of the above mentioned extras rolled in.

Now available on the MODX Extras repo

[MODX-Revo-Boilerplate](http://modx.com/extras/package/modxrevoboilerplate)

[MODX-Revo-Boilerplate-With-Subpackages](http://modx.com/extras/package/modxrevoboilerplatewithsubpackages)


##Additional

* Thanks (as usual) to [Mister John](https://github.com/johnnoel) for a couple of the snippets which accompany the SimpleSearch on the Page Not Found error page.
* The background-size polyfill is from: [Louis Remi on Github](https://github.com/louisremi/background-size-polyfill)
* The box-sizing polyfill is from: [Schepp on Github](https://github.com/Schepp/box-sizing-polyfill)

