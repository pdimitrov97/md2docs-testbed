---
title: Partials
---

# Partials

ERB Partials are automatically converted into Handlebars partial

Simple If statement checking variable value:
```
<%= partial 'about.erb' %>
```

```
{{> about }}
```

Result:

<%= partial 'ruby.html' %>