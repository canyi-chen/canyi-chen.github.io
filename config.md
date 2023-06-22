<!--
Add here global page variables to use throughout your
website.
The website_* must be defined for the RSS to work
-->
@def website_title = "Canyi Chen's Homepage"
@def website_descr = "Canyi Chen's Homepage"
@def website_url   = "http://canyi-chen.github.io/"

@def author = "Canyi Chen"

@def mintoclevel = 2

<!--
Add here files or directories that should be ignored by Franklin, otherwise
these files might be copied and, if markdown, processed by Franklin which
you might not want. Indicate directories by ending the name with a `/`.
-->
@def ignore = ["node_modules/", "franklin", "franklin.pub"]

<!--
Add here global latex commands to use throughout your
pages. It can be math commands but does not need to be.
For instance:
* \newcommand{\phrase}{This is a long phrase to copy.}
-->
\newcommand{\R}{\mathbb R}
\newcommand{\scal}[1]{\langle #1 \rangle}

<!--
Configure
-->
@def  generate_rss = true
@def  rss_website_title = "Canyi Chen"
@def  rss_website_descr = "Canyi Chen's blog"
@def  rss_website_url   = "http://canyi-chen.github.io"
@def  rss_full_content = true