# MODX Revo Boilerplate

## Post installation check list

1. Add new pages:
    * "humans" - type = text, template = empty, richtext = no, published, hidden from menus
    * "robots" - type = text, template = empty, richtext = no published, hidden from menus
    * "Search Results" - template = SearchResults, published, hidden from menus
    * "Page Not Found" - template = PageNotFound, pubslished, hidden from menus
    * sitemap - type = XML, template = empty, richtext = no, published, hidden from menus, content = [[!GoogleSiteMap]]
    * "Thank you" - template = Default, published, hidden from menus

2. Update system settings:
    * Set "error page" setting to the ID of the Page Not Found document
    * Set Site Title
    * If using phpThumbOf/pThumb, set the "Hash thumbnail names" to true/yes
    * Enable friendly URLs, "Use friendly alias path", and "Automatically generate alias"
    * Change the maximum file upload size (default is 1MB, add a 0 to the end to bump up to 10MB)
    * Turn off descriptions for the top menu (much more pleasant!)

3. Via FTP:
    * Rename the ht.access files to .htaccess in "/", "/manager", "/core"
    * Ensure that the following folders exist:
        * /core/components/
        * /assets
            * /assets/components/
            * /assets/templates/
            * /assets/images/
            * /assets/files/
    * Make the following folders all writable:
        * /assets/ and all sub folders
        * /core/cache/
        * /core/components/
        * /core/export/
        * /core/import/
        * /core/package/

4. Via the Manager:
    * Duplicate the "Default" template, and give a sensible name based on your project.
    * Duplicate the "site.head" and "site.foot" chunks and rename sensibly.
    * Edit your new template, and alter the chunk calls for "site.foot" and "site.head" to reflect the new ones you've made
    * Ensure any other chunks/templates you use you duplicate first because upgrading the MODXRevoBoilerplate will OVERWRITE the default chunks/templates every time!
    * If you're not going to be using "default" as the folder for your template, update your templates so that wherever it says &template=`default` it has the correct folder name.

5. If using the JSONDerulo extra, ensure you have added the required details to phpThumb settings as per the [README](http://modx.com/extras/package/jsonderulo)

6. If using TinyMCE, update system settings to NOT output XHTML and make a bit nicer:
    * "tiny.element_format" change from xhtml to html
    * "tiny.convert_newlines_to_brs" - yes

7. If you don't want ".html" added to the end of friendly URLs, go to System/Content Types and blank out the .html extension, then press save

8. If you're not using sessions on the front end of your site (ie - logins, cart, etc) you can set "session_enabled" to 0 on the "web" context settings panel [More details](http://develop.modx.com/blog/2012/04/05/new-for-2.2.1-session-less-contexts/?utm_source=modx_forum&utm_medium=modx&utm_campaign=dev_blog&utm_content=sessionless_contexts)

9. Update your FormIt chunk to have the correct email address/Thank You page ID

10. Update your "articles.aside" duplicated chunk and replace {ID_OF_SEARCH_RESULTS_LANDING_PAGE} with the ID of the Search Results page you created earlier

11. Update your "site.head" duplicated chunk - swap out the placeholder texts with the correct details, or remove the lines if you do not require them

12. These bits might come in handy to add to your MODX .htaccess file in the root of the site (all shamelessly stolen from the [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate):

    ```
    # (!) Using `.htaccess` files slows down Apache, therefore, if you have access
    # to the main server config file (usually called `httpd.conf`), you should add
    # this logic there: http://httpd.apache.org/docs/current/howto/htaccess.html.

    # ##############################################################################
    # # CROSS-ORIGIN RESOURCE SHARING (CORS)                                       #
    # ##############################################################################

    # ------------------------------------------------------------------------------
    # | Cross-domain AJAX requests                                                 |
    # ------------------------------------------------------------------------------

    # Enable cross-origin AJAX requests.
    # http://code.google.com/p/html5security/wiki/CrossOriginRequestSecurity
    # http://enable-cors.org/

    # <IfModule mod_headers.c>
    #    Header set Access-Control-Allow-Origin "*"
    # </IfModule>

    # ------------------------------------------------------------------------------
    # | CORS-enabled images                                                        |
    # ------------------------------------------------------------------------------

    # Send the CORS header for images when browsers request it.
    # https://developer.mozilla.org/en-US/docs/HTML/CORS_Enabled_Image
    # http://blog.chromium.org/2011/07/using-cross-domain-images-in-webgl-and.html
    # http://hacks.mozilla.org/2011/11/using-cors-to-load-webgl-textures-from-cross-domain-images/

    <IfModule mod_setenvif.c>
        <IfModule mod_headers.c>
            <FilesMatch "\.(cur|gif|ico|jpe?g|png|svgz?|webp)$">
                SetEnvIf Origin ":" IS_CORS
                Header set Access-Control-Allow-Origin "*" env=IS_CORS
            </FilesMatch>
        </IfModule>
    </IfModule>

    # ------------------------------------------------------------------------------
    # | Web fonts access                                                           |
    # ------------------------------------------------------------------------------

    # Allow access from all domains for web fonts

    <IfModule mod_headers.c>
        <FilesMatch "\.(eot|otf|ttc|ttf|woff)$">
            Header set Access-Control-Allow-Origin "*"
        </FilesMatch>
    </IfModule>

    # ##############################################################################
    # # INTERNET EXPLORER                                                          #
    # ##############################################################################

    # ------------------------------------------------------------------------------
    # | Better website experience                                                  |
    # ------------------------------------------------------------------------------

    # Force IE to render pages in the highest available mode in the various
    # cases when it may not: http://hsivonen.iki.fi/doctype/ie-mode.pdf.

    <IfModule mod_headers.c>
        Header set X-UA-Compatible "IE=edge"
        # `mod_headers` can't match based on the content-type, however, we only
        # want to send this header for HTML pages and not for the other resources
        <FilesMatch "\.(appcache|crx|css|cur|eot|gif|htc|ico|jpe?g|js|m4a|m4v|manifest|mp4|oex|oga|ogg|ogv|opus|otf|pdf|png|safariextz|svgz?|ttf|vcf|webapp|webm|webp|woff|xml|xpi)$">
            Header unset X-UA-Compatible
        </FilesMatch>
    </IfModule>

    # ##############################################################################
    # # MIME TYPES AND ENCODING                                                    #
    # ##############################################################################

    # ------------------------------------------------------------------------------
    # | Proper MIME types for all files                                            |
    # ------------------------------------------------------------------------------

    <IfModule mod_mime.c>

      # Audio
        AddType audio/mp4                                   m4a f4a f4b
        AddType audio/ogg                                   oga ogg opus

      # Data interchange
        AddType application/json                            json map

      # JavaScript
        # Normalize to standard type (it's sniffed in IE anyways):
        # http://tools.ietf.org/html/rfc4329#section-7.2
        AddType application/javascript                      js

      # Video
        AddType video/mp4                                   f4v f4p m4v mp4
        AddType video/ogg                                   ogv
        AddType video/webm                                  webm
        AddType video/x-flv                                 flv

      # Web fonts
        AddType application/font-woff                       woff
        AddType application/vnd.ms-fontobject               eot

        # Browsers usually ignore the font MIME types and sniff the content,
        # however, Chrome shows a warning if other MIME types are used for the
        # following fonts.
        AddType application/x-font-ttf                      ttc ttf
        AddType font/opentype                               otf

        # Make SVGZ fonts work on iPad:
        # https://twitter.com/FontSquirrel/status/14855840545
        AddType     image/svg+xml                           svgz
        AddEncoding gzip                                    svgz

      # Other
        AddType application/octet-stream                    safariextz
        AddType application/x-chrome-extension              crx
        AddType application/x-opera-extension               oex
        AddType application/x-web-app-manifest+json         webapp
        AddType application/x-xpinstall                     xpi
        AddType application/xml                             atom rdf rss xml
        AddType image/webp                                  webp
        AddType image/x-icon                                cur
        AddType text/cache-manifest                         appcache manifest
        AddType text/vtt                                    vtt
        AddType text/x-component                            htc
        AddType text/x-vcard                                vcf

    </IfModule>

    # ------------------------------------------------------------------------------
    # | UTF-8 encoding                                                             |
    # ------------------------------------------------------------------------------

    # Use UTF-8 encoding for anything served as `text/html` or `text/plain`.
    AddDefaultCharset utf-8

    # Force UTF-8 for certain file formats.
    <IfModule mod_mime.c>
        AddCharset utf-8 .atom .css .js .json .rss .vtt .webapp .xml
    </IfModule>
    ```
