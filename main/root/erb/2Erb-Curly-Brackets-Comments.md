---
title: Curly brackets and Comments
---

# Curly brackets and Comments

## Curly brackets

Markdown project uses <https://handlebarsjs.com/> templating engine to process dynamic content. Handlebars syntax is using curly brackets, so any usage of curly brackets has to be escaped if it is not a Handlebars syntax.

## Comments

ERB comments are automatically converter to Handlebars comments

```
<%# This is an ERB comment>
```

```
{{! This is a Handlebars comment }}
```