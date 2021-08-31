---
title: If Statements
---

# If Statements

ERB If statements are automatically converted into Handlebars expressions

Simple If statement checking variable value:
```
<% if vars.product_name == 'vSphere' %>
```

```
{{# evalExpression "vars.product_name == 'vSphere'" }}
```

More complex If statement with multiple conditions
```
<% if vars.product_name == 'vSphere' || (vars.isCloud == true || vars.product_version > 3) %>
```

```
{{# evalExpression "vars.product_name == 'vSphere' || (vars.isCloud == true || vars.product_version > 3)" }}
```