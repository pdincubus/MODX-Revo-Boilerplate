#MODX Revolution Boilerplate basics

This is mostly a duplicate of the original MODX Revo Boilerplate that I created - but transitioned to SCSS and set up with Grunt for niceness.

##Getting started

This repository is set up for using [Grunt](http://gruntjs.com/). As such, the transport package (from here or from the MODX Extras repo) ONLY contains chunks, snippets and templates and NO assets. Setting Grunt up as per the below will give you lovely minified Javascript and CSS output and allow you to use the lovely SCSS for writing all your styles.

###Prerequisites

1. Node.js
2. This repo.

###Do stuff

* Clone this repo.
* cd /this/dir
* npm install
* grunt -v

##MODX Post Installation Checklist

Stuff you should probably run through manually to make sure things are in tip-top condition. [Checklist](https://github.com/pdincubus/MODX-Revo-Boilerplate/blob/master/Post-Installation-Checklist.md)

##Templates

###Default

Used by default in MODX, very basic HTML structure. Pulls in a head, foot and aside chunk.

###Contact

With configurable FormIt call

###Article & ArticleContainer

For sites using Articles, you'll definitely want new templates for the layout in that section. These two templates have sane defaults and ensures all repeated code is pulled out into head, foot & articleSidebar chunks.

###SearchResults

Create a page, set this template for any searches made from the articles.aside chunk

###PageNotFound

Create a page, set this template, add the system setting for Error Page to point to this new resource


##Chunks

###site.head and site.foot

Beginning and end of the templates. I've added two placeholders - [[+bodyClass]] and [[+template]].

[[+bodyClass]] is useful for complex sites and when passed into the [[$head]] will add that class name to the body tag. Can help save a bunch of extra templates (sometimes).

[[+template]] help make your [[$site.head]] & [[$site.foot]] more generic and easier to chuck into a new site without messing too much. See the BaseTemplate template for how to use.

###articles.aside

Contains most things that were pulled out of the stock Articles templates but are repeated on both container and article template. Nicely wrapped in an aside

###fi.contact-email and fi.contact-form

Install the FormIt extra, and with these two simple chunks you can easily drop a working contact form on any page with little to no customisation required.

###wf.row and wf.outer

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

###robots

Disallows access to a bunch of MODX folders to SpiderBotMonkeys. Also points out the URL of the sitemap (edit this to your URL). You'll need to install the GoogleSiteMap extra to make the sitemap.xml file

###humans

You can pretty much do what you want in this file, but point out developer, designer, technology used, etc.


##Extras

You're going to need the following extras to make all the basics here work:

* [FormIt](http://rtfm.modx.com/extras/revo/formit). For form sending/validation, etc
* [setPlaceholders](https://github.com/oo12/setPlaceholders/). Performs a combination of features from [getResourceField](http://modx.com/extras/package/getresourcefield), [UltimateParent](http://modx.com/extras/package/ultimateparent) and others. Really flexible package and well documented!
* [SimpleSearch](http://rtfm.modx.com/extras/revo/simplesearch). For use on the Page Not Found error page.
* [Wayfinder](http://rtfm.modx.com/extras/revo/wayfinder). Makes menus easy. OR...
* [pdoMenu](http://modx.com/extras/package/pdotools). Almost a drop in replacement for Wayfinder - but supposedly quicker. Part of pdoTools which has other useful things in it too.

Things you're more than likely going to need:

* [pThumb](https://github.com/oo12/phpThumbOf). Crop, thumbnail and alter images automagically. Offers improvements (especially in speed!) over the original phpThumbOf.
* [CodeMirror](http://modx.com/extras/package/codemirror). Syntax highlighting and stuff for anything that isn't a standard content page.
* [getResources](http://rtfm.modx.com/extras/revo/getresources). Useful for all kinds of things, [pdoTools](http://modx.com/extras/package/pdotools) also has a replacement too - pdoResources.
* [GoogleSiteMap](http://rtfm.modx.com/extras/revo/googlesitemap). Generates XML sitemaps for Spiders, etc. Again [pdoTools](http://modx.com/extras/package/pdotools) also has a replacement version, pdoSitemap.
* [VersionX](https://github.com/Mark-H/VersionX2). Content / chunk version tracker extra. Useful for rolling back to a previous version of something.
* [TinyMCE](http://modx.com/extras/package/tinymce). Pretty much the only choice you have for a reasonable text editor in MODX Revo. There is a CKEditor extra but the last time I tried it out it didn't have internal link integration like TinyMCE does. Shame because it's a much nicer RTE. I would heartily recommend [Redactor from ModMore](https://www.modmore.com/?via=231) because it's so much nicer, has great integration and is much better overall than either of the other options.

If you want to set up basic blogging and want something you can just drop in:

* [Articles](http://rtfm.modx.com/extras/revo/articles). This in turn installs a load of extras it needs. Useful for simple blogs.
* [getRelated](http://rtfm.modx.com/extras/revo/getrelated). Goes and sees if it can find content related to the page you're on. Useful in Articles pages.

Other recommendations:

* [ClientConfig](https://www.modmore.com/extras/clientconfig/). Lets you set up global placeholders that your clients can edit easily.
* [JSONDerulo](http://modx.com/extras/package/jsonderulo). Pulls in and outputs JSON feeds for common social feeds.
* [Collections](http://modx.com/extras/package/collections). Hide child pages in the resource tree and gives you a grid for easy searching/viewing of the child pages.



##Additional

* Thanks (as usual) to [Mister John](https://github.com/johnnoel) for a couple of the snippets which accompany the SimpleSearch on the Page Not Found error page.
* The background-size polyfill is from: [Louis Remi on Github](https://github.com/louisremi/background-size-polyfill)
* The box-sizing polyfill is from: [Schepp on Github](https://github.com/Schepp/box-sizing-polyfill)

