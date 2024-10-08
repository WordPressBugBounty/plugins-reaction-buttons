=== Reaction Buttons ===
Tags: feedback, polls, button, comment, widget, sidebar
Requires at least: 3.3
Tested up to: 4.8.2
Stable tag: 2.1.6
License: GPLv2 or later
Donate link: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=MLX3Z7ZD5AJ4Q

Adds buttons for very simple and fast feedback to your post. Inspired by Blogger.

== Description ==

This addon adds buttons below your posts (or somewhere else) to make it easy to get reactions to the post, but without the hassle of writing a whole comment. It makes it easier for the reader to interact with you. The buttons are configurable (how many, what text, position) and simply are counters to how often they were clicked. There is also a widget and a shortcode to show the top x posts with the most clicks for each button.

The idea is inspired by a [blogger feature](http://bloggerindraft.blogspot.com/2008/08/new-feature-reactions.html) and since it's been my first addon, I borrowed the structure from [sociable](http://wordpress.org/extend/plugins/sociable/).

== Installation ==

Nothing fancy, just like any wordpress addon:

1. Upload and unzip the plugin to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress
1. Optionally configure the plugin in the settings tab

* You can also use the widget to show the top x posts with the most clicks for each button in your sidebar. Or alternatively you can use the shortcode [reaction_buttons_most_clicks] to insert the same information somewhere in your post. The default is [reaction_buttons_most_clicks limit_posts=3]. It takes the following arguments:
 * limit_posts: specify the number of posts to show per button. (default 3)
 * excerpt_length: number of words of the article to show as an excerpt. 0 deactivates the excerpt. (default deactivated)
 * only_buttons: comma separated list of buttons to show. Default is to show all
 * show_post_thumb: if the widget should try to display a post thumbnail, true or false (default)
* There is another shortcode for the reaction summary. Engage with your users by including the most clicked button in a summary, e.g. "Most people found this post interesting!" while "interesting" is the most clicked button. Activate it in the options or place it anywhere with the shortcode [reaction_buttons_reaction_summary], which takes summary_text as an argument. In the summary text you can use %s as a place holder for the most clicked button, e.g. [reaction_buttons_reaction_summary summary_text="Most people found this post %s!"] for the example above.

== Frequently Asked Questions ==
= Are there any shortcodes? =
* They are described in the [install tab](http://wordpress.org/extend/plugins/reaction-buttons/installation/).

= My reaction buttons don't update =
* Is your PHP installation new enough? Reaction buttons require at least PHP 5.2.
* Do you use a cache plugin? When the page is cached as soon as you reload the page your vote isn't shown anymore until the cache is cleared. See below.
* (This shouldn't apply since version 2.0.0 anymore.) Do you use any special characters like exclamation marks in your button names?

= I want to deactivate reaction buttons in certain situations =
* Next to the normal options (categories, page types, post options, ...) you can set the global variable $reaction_buttons_deactivate to true e.g. in your plugin or certain theme regions to deactivate reaction buttons during the execution of that code. But don't forget to set it to false again when you are done!

= How can the plugin work with plugins that cache the posts to increase page performance? =
* I added an option to refresh the cache of a page after a button was clicked. But the cache plugin has to be supported by reaction buttons.

= What cache plugins are supported for automatic cache refresh? =
* W3 Total Cache
* Quickcache seems to be working with an easy workaround, check [hengxis solution in the forums](http://wordpress.org/support/topic/adding-support-for-quick-cache?replies=3#post-4573581)
* [Cache Enabler Plugin](https://wordpress.org/plugins/cache-enabler/)

= My plugin isn't listed, can you add support? =
* Sure, use the [wordpress support forums](http://wordpress.org/tags/reaction-buttons?forum_id=10) with a link to the plugin and I'll check it out next time I've got time for the plugin. If you want it fast, check the documentation of the cache plugin and find me the function to delete single page caches. Then it shouldn't be a problem to implement shortly.

= How can I prevent users from voting twice? =
There is an option "Use cookies" in the settings that sends cookies to prevent the user to vote twice on the same post/button (depending on other settings).

It surely is not secure against somebody with bad intent, since they can just delete the cookie and reload the page. If I would save the IP instead, most users could reconnect their internet connection and get a new IP and sometimes on high traffic sites, a user wouldn't be able to react, because somebody else with this IP already clicked. This plugin wants to make it easy to get the users reactions and easy and secure don't work together.  The only secure way is letting them log in, but then you wouldn't get any reactions at all, since 99,9% wouldn't bother. 

== Screenshots ==

1. Shows a german default installation with Reaction Buttons and some clicks on them.
2. Shows the sidebar widget with some dummy data.
3. The graph feature.
4. The graph feature on a small screen.

== Restrictions ==
* When using plugins to cache the pages, the buttons won't be up to date. They will increment through the javascript, but when the page reloads the old count will show again, until the cache is deleted. Check the FAQ on possibilities how to change that.

== Upgrade Notice ==
= 2.1.0 =
* If you use your own CSS, you'll need to update it! This upgrade changes how the reaction data is saved and will convert automatically. But [saving your wordpress database](http://codex.wordpress.org/WordPress_Backups) just in case is a good idea, especially if you might want to ose an old version.

== Changelog ==
= 2.1.6 =
* You should be able to use apostrophes in button names now. 

= 2.1.5 =
* Added support for the [Cache Enabler Plugin](https://wordpress.org/plugins/cache-enabler/), thanks to [@matthiaspabst](https://wordpress.org/support/users/matthiaspabst/).

= 2.1.4 =
* Fixed v2.0 upgrade routine

= 2.1.3 =
* Added filter to conditionally disable the output based on post type. Check [here for an example](https://wordpress.org/support/topic/filter-the-output-for-more-developer-flexibility/). Thanks Matt Cromwell!
* Fixed deprecated syntax when adding the settings menu, thanks flufftron!
* fixed some typos and such

= 2.1.2 =
* Added css-class 'rb-chosen' that is added to the clicked button when only one click is allowed. If you allow to click each button at least once, use the old voted class instead.

= 2.1.1 =
* fixed https related problem (replaced bloginfo() with site_url())

= 2.1.0 =
* added the possibilities to sort the buttons by votes

= 2.0.0 =
* Changed the structure, CSS updates of custom CSS will be necessary.
* Changed the way buttons are saved. They are simply numbered now, so there shouldn't be any problems with special characters. The plugin should automatically convert your reaction counts on the first run to the new system.
* New graph feature, display the votes as a graph instead of buttons. This will possibly look bad and need css updates to match your blogs style.

= 1.8.2 =
* bump for new wordpress version

= 1.8.1 =
* fixed an error in the new widget controls

= 1.8 =
* added option for post thumbs to the widgets
* added show_post_thumb (true/false) to the [reaction_buttons_most_clicks] shortcode
* fixed an error with the [reaction_buttons_most_clicks] shortcode, only_buttons doesn't have to be set anymore to show all buttons

= 1.7 =
* added German translation
* fixed a few errors regarding translation

= 1.6.1 =
* updated a few functions that were deprecated and threw notices on systems running with debug

= 1.6 =
* added the option to show the full post in the widgets
* fixed an error that read the wrong settings variable for the one widget
* fixed an error in the "clicked statistics" page

= 1.5.2 =
* bugfix

= 1.5.1 =
* small error prevented setting the percentage precision to zero

= 1.5 =
* added the option to show percentage values instead of absolute reaction count

= 1.4.4 =
* added a global var to deactivate reaction buttons from other code. See the FAQ for more info.

= 1.4.3 =
* another small bugfix regarding the button statistics widget: Strip shortcodes (like image caption) from the excerpt.

= 1.4.2 =
* small bugfix regarding the button statistics widget: If no button was given, it didn't show any buttons at all instead of all. Thanks [max_Q](http://wordpress.org/support/topic/only-buttons-option-default-to-show-all-not-working?replies=1#post-4135674) for the fix.

= 1.4.1 =
* had to bump the required version of wordpress to 3.3 because of the new button statistics widgets features.

= 1.4 =
* new features in the button statistics widget (and shortcode):
 * option show an excerpt of the post
 * option to only display selected buttons
* Added donate link in the wordpress plugin directory

= 1.3 =
* added a feature to let users vote multiple times
* added a "reaction summary" as option and shortcode: Engage with your users by including the most clicked button in a summary, e.g. "Most people found this post interesting!" while "interesting" is the most clicked button.

= 1.2 =
* changed cookie handling
* added support for deleting the page cache after clicking a button
* supported cache plugin: W3 Total Cache

= 1.1.2 =
* very small java script change

= 1.1.1.1 =
* Well, it's 11.11, so this is the Kölle Alaaf release! :)
* No just kidding, just found a small error in the previous release with the HTML-tagline, fixed now.

= 1.1.1 =
* small update, added the possibility to use HTML in the buttons taqline

= 1.1 =
* added reaction_buttons_click_count($post_id) to include number of reactions per post in own themes. Returns the accumulated number of clicks of the specified post.
* added the possibility to only allow only one vote per post. (Thanks Vlad for most of the code!)
* added the option to show a javascript popup if you try to vote twice.  (Thanks Vlad for the idea and most of the code!)
* added the option to show the results only after the user voted.

= 1.0 =
* small changes for 3.0
* tested with 3.0rc3

= 0.9.9.2 =
* added code for a second widget and statistics page: Show the top x posts with the most overall clicks.

= 0.9.9.1 =
* added code for a statistics page in the backend from Fábio Silva

= 0.9.9 =
* added a shortcode for the widget (show top x posts...)

= 0.9.8 =
* added the possibility to deactivate reaction buttons based on categories.

= 0.9.7 =
* fixed a small error that prevented the ajax update in buttons with more than one whitespace.

= 0.9.6 =
* hopefully solves the [problem with mod_security](http://blog.jl42.de/reaction-buttons/comment-page-1/#comment-812) due to a filename with "cookie" in it... *sigh* 

= 0.9.5.1 =
* removed the possibility to multi vote by clicking really fast (before the ajax response came in)

= 0.9.5 =
* added the shortcode [reaction_buttons] (can be activated in the config)
* added the possibility to add the buttons after the post, above the post, via shortcode and directly in your theme by using a php function. Got the idea for those options from [TYCB](http://wordpress.org/extend/plugins/thanks-you-counter-button/), thanks! :)
* fixed a small settings error

= 0.9.4.1 =
* fixed a bug in the widget, sorting was screwed

= 0.9.4 =
* bugfixes and cleanup on the widget
* small cleanups in the settings

= 0.9.3 (beta) =
* added a widget, that shows the posts with the most clicks for each button.

= 0.9.2 =
* Added the possibility to activate cookies in the backend, so that you can only vote once on that browser. (Anyone with malicios intent can circumvent that pretty easily of course...)

= 0.9.1 =
* fixed issues with spaces
* fixed issues with apostrophs
* some changes in the settings area

= 0.9 =
* First public release.

