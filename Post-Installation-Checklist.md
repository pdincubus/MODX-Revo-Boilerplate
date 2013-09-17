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
