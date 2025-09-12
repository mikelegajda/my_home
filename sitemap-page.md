---
layout: page
title: Site Map
description: "Complete navigation of mikelegajda.com - find all pages, blog posts, and academic publications."
permalink: /sitemap/
---

## Main Navigation

- [Home](/) - About Mikele Gajda and recent work
- [Blog](/blog/) - Articles on operations research and optimization
- [Publications](/publications/) - Academic publications and research
- [CV](/curriculum/) - Professional experience and education
- [About Me](/aboutme/) - Personal background and interests

## Recent Blog Posts

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %d, %Y" }}
{% endfor %}

[View all blog posts →](/blog/)

## Academic Publications

{% for publication in site.publications %}
- [{{ publication.title }}]({{ publication.url }})
{% endfor %}

[View all publications →](/publications/)

## Additional Pages

- [Tags](/tags/) - Browse content by topic
- [Site Map](/sitemap/) - This page
- [RSS Feed](/feed.xml) - Subscribe to updates

## Contact & Social

- Email: [mikelegajda@gmail.com](mailto:mikelegajda@gmail.com)
- LinkedIn: [mikele-gajda](https://linkedin.com/in/mikele-gajda)
- GitHub: [mikelegajda](https://github.com/mikelegajda)
- Google Scholar: [Profile]({{ site.social-network-links.google_scholar }})