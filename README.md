# Customize Content Widgets
Extension to the Customize Posts and Shortcake plugins to add post/page-specific widget areas in content (an implementation of content blocks).

Ideas for how to implement content blocks as widgets in the Customizer, powered by [Customize Posts](https://github.com/xwp/wp-customize-posts), [Shortcake](https://github.com/wp-shortcake/shortcake), and (ideally) [JS Widgets](https://github.com/xwp/wp-js-widgets):

1. Register a new shortcode for `widget_area` which takes a single argument to indicate the widget area to embed (sidebar ID). (Additional shortcake attributes arguments could also be supplied according to the normal sidebar args passed into `register_sidebar()`).
2. Create a new `content_widget_area` post type to store the widget configurations for the widget areas (sidebars) registered for a given post/page.
3. In the Shortcode UI, provide a dropdown of all the existing registered sidebars with an option to create a new dynamic one.
4. Add a new “Add Widget Area” media button as a shortcut for opening the media modal and selecting the widget area to embed.
5. Implement the Shortcode UI (Shortcake) preview extensions to allow the `widget_area` to be presented in the visual editor as a list of widgets, similar to how they appear in a collapsed state on the admin page or Customizer pane
6. The TinyMCE view on the widget area preview should have an Edit link to change which widget area is displayed, and Edit button to open the sidebar Customizer section, and add an edit button with each widget listed in the TinyMCE view which provides a deep link to the widget control in the Customizer sidebar section. Note than when the sidebar/widget is focused in the Customizer, the back button should be overridden to return the user back to the post being edited, instead of the list of sidebars. See [#32683](https://core.trac.wordpress.org/ticket/32683#comment:6).
7. Implement lazy-loading of widget settings and sidebars so widgets and sidebars needn't all be exported up-front when the Customizer first loads (see [#28580](https://core.trac.wordpress.org/ticket/28580)).
8. Make sure the Shortcode TinyMCE view in the post is synced when the corresponding sidebar and widgets are updated.

For background, see:

* [Customize Posts: Page Builder / Content Editor in Customizer](https://wordpress.org/support/topic/page-builder-content-editor-in-customizer?replies=11#post-8395850)
* [Shortcake: Content Blocks: Shortcodes & Widgets](https://github.com/wp-shortcake/shortcake/issues/585)
