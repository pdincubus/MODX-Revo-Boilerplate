#MODX Revolution Boilerplate basics

A bunch of stuff to quickly get some sensible basics into a new [MODX Revolution](http://modx.com/) install. There's a folder for each type of resource. Simply make a new resource of that particular type and copy in the code.

Now available on the MODX Extras repo

[MODX-Revo-Boilerplate](http://modx.com/extras/package/modxrevoboilerplate)

[MODX-Revo-Boilerplate-With-Subpackages](http://modx.com/extras/package/modxrevoboilerplatewithsubpackages)

##Templates

###BaseTemplate

Used by default in MODX, very basic HTML structure. Pulls in a head and foot chunk.

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

The templates and chunks in this repository assume you've put these files in the same place. If not, make sure you update the relevant paths.

###CSS

I use LESS just about all the time.

Includes the HTML5 Boilerplate normalise CSS (with a few tweaks), Internet Explorer HTC behaviour file for border-box box-sizing method, clearfixes, classes, and basic print styles.

###js

Includes Modernizr for YepNope and making people think that old versions of Internet Explorer are futuristic. Kind of. Also includes local version jQuery for fallback should the CDN download fail, and jQuery Easing for nicer animations.

Selectivizr is also in there for those who want its functionality to support older versions of *cough* Internet Explorer.


##Chunks

###head and foot

Beginning and end of the templates. I've added two placeholders - [[+bodyClass]] and [[+template]].

[[+bodyClass]] is useful for complex sites and when passed into the [[$head]] will add that class name to the body tag. Can help save a bunch of extra templates (sometimes).

[[+template]] help make your [[$head]] & [[$foot]] more generic and easier to chuck into a new site without messing too much. See the BaseTemplate template for how to use.

###standard-sidebar

Chuck everything in here that you would have in your aside.

###article-sidebar

Contains most things that were pulled out of the stock Articles templates but are repeated on both container and article template. Nicely wrapped in an aside

###fi.contact-email and fi.contact-form

Install the FormIt extra, and with these two simple chunks you can easily drop a working contact form on any page with little to no customisation required.

###wf.row-tpl

Wayfinder's default setup for outputting a menu item needs a bit of tweaking since we've used the link_attributes to apply a class to the body tag.

###quip.comment

Replacement, lovely and trimmed down version of the standard Quip chunk

###quip.add-comment, articles-lLatest-post-tpl, archive-group-by-year, article-row-tpl

See above.



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


##Extras

I generally use the following extras most of the time:

* Ace (code editor). <del>A lot better than CodeMirror</del>. The new version of CodeMirror is a lot better than the previous one. So either of these are decent. CodeMirror also has the option for colour schemes for syntax highlighting.
* Articles. This in turn installs a load of extras it needs
* Big Brother. A Google Analytics dashboard widget.
* FormIt. For form sending/validation, etc
* getRelated. Goes and sees if it can find content related to the page you're on. Useful in Articles pages.
* getResourceField. Useful for grabbing one bit of data from one single page. Kind of get resources, but blinkered.
* getResources. Useful for all kinds of things.
* GoogleSiteMap. Generates XML sitemaps for Spiders, etc
* [JSONDerulo](http://modx.com/extras/package/jsonderulo23). Pulls in and outputs JSON feeds for common social feeds.
* phpThumbOf. Crop, thumbnail and alter images automagically.
* SimpleSearch. For use on the Page Not Found error page.
* UltimateParent. Searches up branches to find parent pages at a chosen level. I use this for the bodyClass placeholder mostly.
* Wayfinder. Makes menus easy.


##Transport Package

This is *untested*. Be careful, the sky may fall down.

* If you *only* want the snippets, chunks, assets and templates - use the default package.
* If you want the *full* package - install the "subpackages" transport package. This includes many of the above mentioned extras rolled in.

Assets are not included in this package. To install, FTP to your /core/packages/ directory, go to Package Management and instead of clicking "Download Extras", click the arrow and choose "Search Locally For Packages".

You _need_ to remember to _change_ the SimpleSearch "landing page" id, as well as things for FormIt in the fi.contact-form chunk.

Then install in the usual way once the package is detected.

##Additional

Thanks (as usual) to [Mister John](https://github.com/johnnoel) for a couple of the snippets which accompany the SimpleSearch on the Page Not Found error page.
