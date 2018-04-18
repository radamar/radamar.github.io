---
title: "ShadowFox; a dark theme for Firefox web browser, and an autohiding sidebar"
---

## Install Firefox and required extensions.
First, check which version of Firefox web browser is installed on your system, Firefox > Settings > About Firefox. This modification will require Firefox version 57+ a.k.a. Firefox Quantum.
Alternatively, in a terminal window: 
{% highlight shell %}
firefox -v
{% endhighlight %}

Next Up, if you want to have a tabs sidebar instead of a tab bar at the top of the browser, you will need to install piroor's Tree Style Tabs extension from [Firefox addons][1].

## Find your firefox profile folder.

You will now need to find your user's chrome folder which will be located at 
`~/.mozilla/firefox/_your-profile_/chrome`
It might be different in your case.

{% highlight shell %}
firefox about:profiles
{% endhighlight %}
In this tab you can either create a new profile or proceed with the default one, open the root directory and go to the chrome folder. If you don't see a userChrome.css, userContent.css inside, you can create them.

## Clone ShadowFox and UserChrome-Tweaks from GitHub.
You will need to have git installed, and a few other packages. You can use your favorite package manager, or chocolatey on Windows systems.
{% highlight shell %}
pacman -S git
{% endhighlight %}

Go to your profile directory and:
{% highlight shell %}
cd ~/.mozilla/firefox/your-profile/chrome/
git clone https://github.com/radamar/UserChrome-Tweaks.git UserChrome-Tweaks
git clone https://github.com/overdodactyl/ShadowFox.git ShadowFox
{% endhighlight %}

## Make a new file imports_userChrome.css and imports_userContent.css
`~/.mozilla/firefox/_your-profile_/chrome/imports_userChrome.css`
{% highlight css %}
@import "ShadowFox/css/common-files/color_variables.css";
@import "ShadowFox/css/common-files/trees.css";
@import "ShadowFox/css/common-files/radios_checkboxes.css";

@import "ShadowFox/css/userChrome-files/about_firefox.css";
@import "ShadowFox/css/userChrome-files/address_searchbar.css";
@import "ShadowFox/css/userChrome-files/bookmarks_popup.css";
@import "ShadowFox/css/userChrome-files/common_dialog.css";
@import "ShadowFox/css/userChrome-files/context_menus.css";
@import "ShadowFox/css/userChrome-files/customization_page.css";
@import "ShadowFox/css/userChrome-files/findbar.css";
@import "ShadowFox/css/userChrome-files/library.css";
@import "ShadowFox/css/userChrome-files/navbar_menus.css";
@import "ShadowFox/css/userChrome-files/page_info.css";
@import "ShadowFox/css/userChrome-files/remove_bookmarks_bottom_border.css";
@import "ShadowFox/css/userChrome-files/remove_white_flash.css";
@import "ShadowFox/css/userChrome-files/secure_connection_colors.css";
@import "ShadowFox/css/userChrome-files/sidebar.css";
@import "ShadowFox/css/userChrome-files/status_panel.css";
@import "ShadowFox/css/userChrome-files/tab_line_colors.css";

/* Your imports */
@import "UserChrome-Tweaks/sidebar/auto-hide-sidebar-tst.css";
@import "UserChrome-Tweaks/sidebar/hide-sidebar-header.css";
@import "UserChrome-Tweaks/findbar/compact-findbar-on-top.css";
@import "UserChrome-Tweaks/findbar/hide-status.css";
@import "UserChrome-Tweaks/misc/hide-statuspanel.css";
@import "UserChrome-Tweaks/hamburger/remove-sync.css";
@import "UserChrome-Tweaks/navbar/hide-back-forward.css";
@import "UserChrome-Tweaks/tabs/hide-tabs-linux-titlebar.css";
@import "UserChrome-Tweaks/context-menu/remove-send-to-device.css";

{% endhighlight %}

`~/.mozilla/firefox/_your-profile_/chrome/imports_userContent.css`
{% highlight css %}
/* Required for all users */
@import "ShadowFox/css/common-files/color_variables.css";
@import "ShadowFox/css/common-files/trees.css";
@import "ShadowFox/css/common-files/radios_checkboxes.css";

@import "ShadowFox/css/userContent-files/about_pages.css";
@import "ShadowFox/css/userContent-files/amo_store.css";
@import "ShadowFox/css/userContent-files/directory_listings.css";
@import "ShadowFox/css/userContent-files/manifest.css";
@import "ShadowFox/css/userContent-files/pdf.css";
@import "ShadowFox/css/userContent-files/raw_githubusercontent.css";
@import "ShadowFox/css/userContent-files/view_source.css";


/* Import Relevant webextension tweaks here
 * IMPORTANT: If used, change the Internal UUID in the corresponding css file */
@import "ShadowFox/css/userContent-files/webextension-tweaks/noscript.css";
@import "ShadowFox/css/userContent-files/webextension-tweaks/tree_style_tab.css";
@import "ShadowFox/css/userContent-files/webextension-tweaks/ublock_origin.css";
@import "ShadowFox/css/userContent-files/webextension-tweaks/ubo_scope.css";
@import "ShadowFox/css/userContent-files/webextension-tweaks/umatrix.css";
@import "ShadowFox/css/userContent-files/webextension-tweaks/vim_vixen.css";

/* Your imports */
{% endhighlight %}

# You can also copy these files to userChrome.css and userContent.css respectively as they are the same. However, at current time the import statements are buggy and you may be required to follow the next step if there are any issues.

{% highlight shell %}
cp imports_userChrome.css userChrome.css
cp imports_userContent.css userContent.css
{% endhighlight %}

## Inline and optimise the css.
Follow this step, If the imports statements are buggy, or if you want to optimise the css files by inlining the css.

{% highlight shell %}
pacman -S npm nodejs 
npm install -g postcss gulp-cli postcss-cssnano postcss-import
{% endhighlight %}

Make a bash script in the chrome directory itself:
`update.sh`
{% highlight shell %}
#!/usr/bin/zsh
cp userChrome.css userChrome.css.bak
cp userContent.css userContent.css.bak
postcss imports_userChrome.css -u postcss-import -u cssnano -o userChrome.css
postcss imports_userContent.css -u postcss-import -u cssnano -o userContent.css
{% endhighlight %}

Grant execute permissions to the user.
{% highlight shell %}
chmod u+x update.sh

{% endhighlight %}

Execute the update.sh script when you have to update the tweaks.
{% highlight shell %}
./update.sh
{% endhighlight %}
## More about userChrome.css and userContent.css tweaks.
You can learn more about userChrome.css at [www.userChrome.org][2].

Learn more about ShadowFox at their [Github page][4], See the UserChrome-Tweaks [repository][3].

[1]: https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/

[2]: https://www.userchrome.org/

[3]: https://github.com/Timvde/UserChrome-Tweaks.git

[4]: https://github.com/overdodactyl/ShadowFox.git

[5]: https://github.com/radamar/UserChrome-Tweaks.git
