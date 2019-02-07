# Template Heirarchy

## Description

In this lesson you will learn how WordPress Template Hierarchy is a powerful system that allows you to create front-end templates for many types of WordPress pages. This walk-through will teach you what the WordPress Template Hierarchy is and how to use it to serve a variety of pages.

## Objectives

After completing this lesson, you will be able to:

*   Use WordPress Templates to define the output in various ways.
*   Identify which template file(s) WordPress uses.
*   Create a template.

## Prerequisite Skills

You will be better equipped to work through this lesson if you have:

*   Basic knowledge of HTML and [CSS](https://make.wordpress.org/training/handbook/lesson-plans/theme-school/intro-to-css/)
*   Basic knowledge of [installing and activating WordPress themes](https://make.wordpress.org/training/handbook/lesson-plans/user-lessons/choosing-and-installing-a-theme/)
*   Understanding of how folders and files are structured
*   Ability to edit files with a text editor

## Assets

*   [Twenty Fourteen Theme](http://wordpress.org/themes/twentyfourteen "Twenty Fourteen Theme")
*   [Template Hierarchy Chart](http://codex.wordpress.org/File:Template_Hierarchy.png) (.png)
*   [Interactive Diagram of the WordPress Template Hierarchy](http://wphierarchy.com/)

## Screening Questions

*   Are you familiar with installing and activating themes via the WordPress Dashboard?
*   Do you understand the parts that make up the anatomy of a WordPress Theme?
*   Do you have at least a basic knowledge of HTML and CSS?
*   Do you feel comfortable using a text editor to edit code?
*   Will you have a locally or remotely hosted sandbox WordPress site to use during class?

## Teacher Notes

*   Performing a live demo while teaching the steps to create WordPress Templates is crucial to having the material “click” for students.
*   It is easiest for students to work on a locally installed copy of WordPress. Set some time aside before class to help students with installing WordPress locally if they need it. For more information on how to install WordPress locally, please visit our [Teacher Resources page](http://make.wordpress.org/training/teacher-resources/).
*   The preferred answers to the screening questions are “yes.” If students reply “no” to all 5 questions they may not be ready for this lesson.

## Hands-on walk-through

### Introduction

Today you are going to learn how to use WordPress Templates to define the output in different ways. We will look at which template file(s) WordPress uses when it displays a certain type of page. As a designer, you may want to style some types of pages in a different way than the standard page presentation. This is where WordPress Templates are used, so understanding how WordPress selects templates to display its various pages is key.

### Warm up Discussion

*   Why is this good for blogs? CMS Sites?
*   What do you think the Template Hierarchy is?
*   Why learn about Template Hierarchy?

* * *

### Before You Start

The #1 Rule of WordPress development is to **never change WordPress files.** **This means do not edit:**

*   WordPress core files
*   Plugin files
*   Theme files*

**Why?** **Theme updates wipe out changes** If a modified theme is updated, all customization will be overwritten. Many of us learned this the hard way as beginners. **Themes break** If theme files are edited and break past the “hit undo” point, you are stuck with a broken theme. **WordPress and WordPress Plugins may not may not work with theme hacks** Elements that WordPress and WordPress plugins look for in a theme may be accidentally removed and then no longer work. **So how do you customize a WordPress theme?**

*   Use a starter theme or create your own one from scratch.
*   Create a **Child Theme** that is a “**child**” of another theme (the Parent Theme).

*Exception: starter themes that have been intentionally created by theme builders for you to modify

* * *

### How WordPress selects templates to generate web pages

WordPress uses the [Query String](http://codex.wordpress.org/Glossary#Query_String "Glossary") to decide which template or set of templates should be used to display the page. The query string in your URI comes after the initial question mark and may contain a number of parameters separated by ampersands. Simply put, WordPress searches down through the Template Hierarchy until it finds a matching template file. To decide which template file to use, WordPress:

1.  matches every query string to a query type to decide which page is being requested (such as, a search page, a category page, etc.)
2.  selects the template in the order determined by the Template Hierarchy
3.  looks for template files with specific names in the current theme’s directory and uses the **first matching template file** as specified by the hierarchy.

With the exception of the basic index.php template file, you can choose whether you want to implement a particular template file or not. If WordPress cannot find a template file with a matching name, it will skip to the next file in the hierarchy. If WordPress cannot find any matching template file, the theme’s index.php file will be used.

* * *

### Visual Overview

The following diagram shows which template files are called to generate a WordPress page based on the WordPress Template Hierarchy. [caption id="attachment_822" align="alignnone" width="632"][![Template Hierarchy Chart](http://make.wordpress.org/training/files/2014/09/template-hierarchy-retina-light-1024x640.jpg)](http://make.wordpress.org/training/files/2014/09/template-hierarchy-retina-light.jpg) Template Hierarchy Chart[/caption] [Interactive Diagram of the WordPress Template Hierarchy](http://wphierarchy.com/)

### Examples

If your blog is at http://example.com/blog/ and a visitor clicks on a link to a category page such as http://example.com/blog/category/unicorns/, WordPress looks for a template file in the current theme’s directory that matches the category’s ID to generate the correct page as follows:

1.  WordPress looks for a template file in the current theme’s directory that matches the category’s slug. Here the category slug is “unicorns,” so WordPress looks for a template file named category-unicorns.php.
2.  If category-unicorns.php is missing and the category’s ID is 4, WordPress looks for a template file named category-4.php.
3.  If category-4.php is missing, WordPress will look for a generic category template file, category.php.
4.  If category.php does not exist, WordPress will look for a generic archive template, archive.php.
5.  If archive.php is also missing, WordPress will fall back on the main theme template file, index.php.

## The Template Hierarchy In Detail

In this section we'll take a look at the Template Hierarchy in detail, and learn about the order in which each Template file is called for each Query type. **Home Page Display** This template file is used to render the Blog Posts Index, whether the user is on the site's front page or on a static page. Note: on the Site Front Page, the Front Page Display Template below takes precedence over the Blog Posts Index (Home) template.

1.  home.php
2.  index.php

**Front Page Display** This template file is used to render the Site Front Page, whether the front page displays the Blog Posts Index or a static page. The Front Page template takes precedence over the Blog Posts Index (Home) template.

1.  front-page.php - Used for both **your latest posts** or **a static page** as set in the **front page displays** section of [Settings](http://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") -> [Reading](http://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel")
2.  The [Page display](http://codex.wordpress.org/Template_Hierarchy#Page_display) is used when the **front page** is set in the **front page displays** section of [Settings](http://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") -> [Reading](http://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel")
3.  The [Home Page display](http://codex.wordpress.org/Template_Hierarchy#Home_Page_display) is used when the **posts page** is set in the **Front page displays** section of [Settings](http://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") -> [Reading](http://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel")

**Single Post Display** This template file is used to render a single post page.

1.  single-{post_type}.php - If the [post type](http://codex.wordpress.org/Post_Types "Post Types") is "product", WordPress will look for single-product.php.
2.  single.php
3.  index.php

**Page Display** This template file is used to render a static page ("page" post-type).

1.  custom template file - The [Page Template](http://codex.wordpress.org/Page_Templates "Page Templates") assigned to the page. See [get_page_templates()](http://codex.wordpress.org/Class_Reference/WP_Theme#Get_Custom_Page_Templates "Class Reference/WP Theme").
2.  page-{slug}.php - If the page slug is **recent-news**, WordPress will look for page-recent-news.php
3.  page-{id}.php - If the page ID is "6", WordPress will look for page-6.php
4.  page.php
5.  index.php

**Category Display** This template file is used to render a Category Archive Index page

1.  category-{slug}.php - If the category's slug is "news", WordPress will look for category-news.php
2.  category-{id}.php - If the category's ID is "6", WordPress will look for category-6.php
3.  category.php
4.  archive.php
5.  index.php

**Tag Display** This template file is used to render a Tag Archive Index page.

1.  tag-{slug}.php - If the tag's slug is "sometag", WordPress will look for tag-sometag.php
2.  tag-{id}.php - If the tag's ID is "6", WordPress will look for tag-6.php
3.  tag.php
4.  archive.php
5.  index.php

**Custom Taxonomies Display** This template file is used to render the Archive Index page for a [Custom Taxonomy](http://codex.wordpress.org/Taxonomies "Taxonomies")

1.  taxonomy-{taxonomy}-{term}.php - If the taxonomy is "sometax", and taxonomy's term is "someterm" WordPress will look for taxonomy-sometax-someterm.php. In the case of Post Formats, the taxonomy is 'post_format' and the terms are 'post-format-{format}. i.e. taxonomy-post_format-post-format-link.php
2.  taxonomy-{taxonomy}.php - If the taxonomy is "sometax", WordPress will look for taxonomy-sometax.php
3.  taxonomy.php
4.  archive.php
5.  index.php

**Custom Post Types Display** This Template file is used to render the Archive Index page for a [Custom Post Types](http://codex.wordpress.org/Post_Types "Post Types")

1.  archive-{post_type}.php - If the [post type](http://codex.wordpress.org/Post_Types "Post Types") is "product", WordPress will look for archive-product.php.
2.  archive.php
3.  index.php

(For rendering a single custom post type, refer to the Single Post display section above.) **Author Display** This Template file is used to render an Author Archive Index page

1.  author-{nicename}.php - If the author's nice name is "Rami", WordPress will look for author-rami.php.
2.  author-{id}.php - If the author's ID is "6", WordPress will look for author-6.php.
3.  author.php
4.  archive.php
5.  index.php

**Date Display** This template file is used to render a Date-Based Archive Index page.

1.  date.php
2.  archive.php
3.  index.php

**Search Result Display** This template file is used to render a Search Results Index page.

1.  search.php
2.  index.php

**404 (Not Found) Display** This template file is used to render a Server 404 error page.

1.  404.php
2.  index.php

**Attachment Display** This template file is used to render a single attachment ("attachment" post-type) page.

1.  MIME_type.php - it can be any [MIME type](http://en.wikipedia.org/wiki/Internet_media_type "http://en.wikipedia.org/wiki/Internet_media_type") (image.php, video.php, application.php). For text/plain, in order:
    1.  text.php
    2.  plain.php
    3.  textplain.php
2.  attachment.php
3.  single-attachment.php
4.  single.php
5.  index.php

* * *

### Filter Hierarchy

The WordPress templates system allows you to filter the hierarchy. The filter (located in the [get_query_template()](http://codex.wordpress.org/Function_Reference/get_query_template "Function Reference/get query template") function) uses this filter name: "{$type}_template" where $type is the file name in the Hierarchy without the .php extension. Full list:

*   index_template
*   404_template
*   archive_template
*   author_template
*   category_template
*   tag_template
*   taxonomy_template
*   date_template
*   home_template
*   front_page_template
*   page_template
*   paged_template
*   search_template
*   single_template
*   text_template, plain_template, text_plain_template (all mime types)
*   attachment_template
*   comments_popup

### <span class="mw-headline">Example</span>

For example, let's take the default Author Hierarchy:

*   author-{nicename}.php
*   author-{id}.php
*   author.php

To add author-{role}.php before author.php we can manipulate the actual hierarchy using the 'author_template' hook. This allows a request for /author/username where username has the role of editor to display using author-editor.php if present in the current themes directory.

```PHP
function author_role_template( $templates='' ) {
	$author = get_queried_object();
	$role = $author->roles[0];
	if( !is_array( $templates ) && !empty( $templates ) ) {
		$templates = locate_template( array( "author-$role.php", $templates ), false );
	} elseif( empty( $templates ) ) {
		$templates = locate_template( "author-$role.php", false );
	} else {
		$new_template = locate_template( array( "author-$role.php" ) );
		if( !empty( $new_template ) ) 
			array_unshift( $templates, $new_template );
	}
	return $templates;
}
add_filter( 'author_template', 'author_role_template' );
```

## Exercises

**Create a Template for the category "Movies"**

*   Which file must you create and how do you name it?
*   Add a subtitle under the archive-title.
*   Check your work (yoursite.url/category/movies/)

## Quiz

**Which template is not used when the site's front page is accessed?**

1.  index.php
2.  front-page.php
3.  home.php
4.  single.php

**Answer:** 4. single.php

**Can you customize the archive output from a custom post type?**

1.  Yes
2.  No

**Answer:** 1. Yes

**Which template is the last instance for fallback?**

1.  home.php
2.  single.php
3.  index.php
4.  archive.php

**Answer:** 3. index.php

## Additional Resources

[The Loop](https://developer.wordpress.org/themes/basics/the-loop/) @ developer.wordpress.org
