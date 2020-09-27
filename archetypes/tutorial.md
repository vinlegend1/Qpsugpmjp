---
title: "{{ replace .Name "-" " " | title }}" # Title of the blog post.
date: {{ .Date }} # Date of post creation.
description: "tutorial description." # Description used for search engine.
featured: true # Sets if post is a featured post, making it appear on the sidebar. A featured post won't be listed on the sidebar if it's the current page
draft: true # Sets whether to render this page. Draft of true will not be rendered.
toc: true # Controls if a table of contents should be generated for first-level links automatically.
# menu: main
featureImage: "/default.jpg" # Sets featured image on blog post.
thumbnail: "/default.jpg" # Sets thumbnail image appearing inside card on homepage.
shareImage: "/default.jpg" # Designate a separate image for social media sharing.
codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
categories:
  - Tutorial
tags:
  - Tag_name1
  - Tag_name2
---