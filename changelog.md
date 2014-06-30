For all info: https://github.com/pdincubus/MODX-Revo-Boilerplate/

#Most recent additions

##1.3.0
    * update setPlaceholder calls all round
    * update modernizr to 2.7.2
    * update jQuery to 1.11.0 and 2.1.0
    * make the contact form configurable
    * new contact template
    * replace Wayfinder call with pdoMenu
    * new outerTpl chunk for pdoMenu/Wayfinder
    * update viewport meta tag to match HTML5BP
    * Only show Quip stuff if comments_enabled is set on article template
    * remove site.aside from templates

##1.2.0
    * Updated head chunk for new modernizr and new style (NO IE CONDITIONAL COMMENTS!) html setup from HTML5 Boilerplate
    * Updated humans.txt to match HTML5BP
    * Updated LESS files to simplify a bit
    * New modernizr in default/js/lib template folder on install

##1.1.1
    * Changed #main to HTML5 main element
    * Tweak to sidebars
    * LESS changes for main element, more auto clearfixes
    * Reduced robots.txt to avoid giving away MODX directory names
    * Post Installation Checklist: https://github.com/pdincubus/MODX-Revo-Boilerplate/blob/master/Post-Installation-Checklist.md

##1.1
    * ALWAYS BACK UP YOUR CUSTOMISATIONS BEFORE UPGRADING - Any upgrades will overwrite all the default installed snippets/chunks/templates!
    * Refactored a lot of stuff
    * Swapped out Page Not Found and Search Results into templates to avoid breakage when editing the resource directly
    * Re-jigged all the LESS to make more logical sense - splitting them apart into folders based on what they're for, etc
    * Templates allow you to set multiple placeholders before head and foot chunks are called, makes things more flexible
    * Added post installation checklist document for all the bits you might forget to sort!
    * Updated docs

##1.0
    * Renamed most chunks to make it a bit more logcial
    * updates to jQuery versions
    * Added new style Google analytics code to [[$site.foot]]
    * Refactored LESS directories and config
    * IF YOU ARE UPGRADING FROM THE PREVIOUS VERSION - make sure you have backed up things first!!!
    * new extras bundles for subpackages version: swapped out getResourceField and UltimateParent for setPlaceholders, swapped out phpThumbOf for new pThumb extra

##0.9b
    * Updated a bunch of everything. New test transport package
