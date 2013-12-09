# Modified 'Kr/Flask' Sphinx theme

This repository is a modified "Kr" Sphinx theme from @kennethreitz, which was
in turn modfied from @mitsuhiko's theme used for Flask & related projects.

I named the theme itself back to "flasky" (reflecting that it's relatively
generic and not used for Kenneth's own projects, but my own or anybody else's
use) and tried to polish it up. To wit, changes from Kenneth's theme:

* No 'small' theme since I didn't need it & wanted to remove noise;
* Minor style tweaks, such as ensuring code blocks left-align with regular text
  blocks (in Kenneth's theme they are dedented too far);
* Additional customization hooks, such as header/link/etc colors;
* Improved documentation for all customizations (pre-existing & new).

To use:

1. Use this folder as the `_themes` subdirectory of your Sphinx project (copy
   it, use a git submodule, whatever.)
1. Enable the 'flasky' theme in your `conf.py`:

       import os
       import sys
       
       sys.path.append(os.path.abspath('_themes'))
       html_theme_path = ['_themes']
       html_theme = 'flasky'
       html_sidebars = {
           'index': [
               'sidebar.html', 'sourcelink.html', 'searchbox.html'
           ],
           '**': [
               'sidebar.html', 'localtoc.html', 'relations.html',
               'sourcelink.html', 'searchbox.html'
           ]
       }

    * Modify the call to `abspath` if your `_themes` folder doesn't live right
    next to your `conf.py`.
    * Feel free to adjust `html_sidebars` as desired - the theme is designed
    assuming you'll have `sidebar.html` activated, but otherwise it doesn't
    care much. See [the Sphinx
    docs](http://sphinx-doc.org/config.html#confval-html_sidebars) for details.

1. If desired, add a final option to `conf.py` overriding one or more theme
   options, like in this example (*note*: snippet doesn't include all possible
   options, see following list!):

       html_theme_options = {
           'logo': 'static/logo.png',
           'github_user': 'bitprophet',
           'github_repo': 'sphinx-theme',
       }

   The available theme options (which are all optional) are as follows:

   * `logo`: Relative path (from `$PROJECT/_themes/`) to a logo image, which
   will appear in the upper left corner above the name of the project.
       * **Note:** while this is technically optional, things will look
       slightly off without one. We recommend coming up with a logo and making
       it approximately 224x200 pixels. See e.g.
       [Requests](http://docs.python-requests.org/en/latest/_static/requests-sidebar.png).
   * `description`: Text blurb about your project, to appear under the logo.
   * `github_*`: Used to link to your Github
   repo via the [Github Buttons](http://ghbtns.com/) service. Specific sub-keys
   are as follows - when not specified, values behave exactly the same as in
   [Github Buttons' README](https://github.com/mdo/github-buttons#usage):
      * `user`, `repo`: The user and repo name, so e.g. `kennethreitz/requests`
      would have a `github_user` of `kennethreitz` and `github_repo` of
      `requests`. **Both of these are required if you want a Github button to
      appear.**
      * `type`: Defaults to `watch`.
      * `count`: Defaults to `true` (**note:** `"true"`, the string, not
      `True`, the Python value for truth.)
   * `gittip_user`: Set to your [Gittip](https://gittip.com) username if you
   want a Gittip 'Donate' section in your sidebar.
   * `touch_icon`: Path to an image to be used for an iOS application icon, for
   when pages are saved to an iOS device's home screen via Safari.
