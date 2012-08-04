DAS-SCRIBE

Stupid-simple static content system.

Simple use:

    $ das-scribe posts/ /var/www/blog/ --template=post_template.html

posts should be a file consisting of sub-directories, each containing a post in
.md format and any other files needed for it. Example:

    posts/2012/03/24/late_march_stuff.md
    posts/2012/03/24/spring.png
    posts/2012/03/25/late_march_addendum.md
    posts/2012/05/05/cinco_de_mayo.md
    posts/2012/05/05/pinata.png

This will produce:

    /var/www/blog/2012/03/24/late_march_stuff.html
    /var/www/blog/2012/03/24/spring.png
    /var/www/blog/2012/03/25/late_march_addendum.html
    /var/www/blog/2012/05/05/cinco_de_mayo.html
    /var/www/blog/2012/05/05/pinata.png

It is assumed alphabetic sort order for the post directories is chronological
order.

The template file has template variables that are filled in, in a django-like
syntax:

* `{{content}}`: Replaced with the markdown-processed post.
* `{{newer_link}}`: Replaced with the url of the next post. The format of this
  url is `<link_prefix>/path/to/post`; the option `--link_prefix` specifies the
  prefix to use.
* `{{older_link}}`: Replaced with the url of the prev post. The format of this
  url is `<link_prefix>/path/to/post`; the option `--link_prefix` specifies the
  prefix to use.
