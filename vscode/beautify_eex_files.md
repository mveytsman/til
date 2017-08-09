# Beautify .eex files

In order to have working formating for `html.eex` files

1) Install the `Beautify` extension
2) Put the following in `~/.jsbeautifyrc`
```json
{
	"html": {
		"void_elements": ["%", "%=", "area", "base", "br", "col", "embed", "hr", "img", "input", "keygen", "link", "menuitem",	"meta", "param", "source", "track", "wbr", "!doctype", "?xml", "?php", "basefont", "isindex"]
	}
}
```

The above will make the `<%= %>` and `<% %>` tags be formatted without creating a new indention level.

## Templates inside quotes

One problem you'll have to deal with is that 
```html
<a href="<%= fun("string") %>">...</a>
```
will be formatted to
```html
<a href="<%= fun(" string ") %>">...</a>
```

This is because the quotes inside the `<%= %>` tag are treated as quotes inide the `<a>` tag by the formatter. You can see the issue in the broken syntax highlighting above.

If this was Ruby, I would say just use single quotes for strings inside interpolated expressions in this situation, but in Elixir they are charlists instead of binaries which will break things. Instead, either do a sigil
```html
<a href="<%= fun(~s{string}) %>">...</a>
```
or use single quotes in the html
```html
<a href='<%= fun("string") %>'>...</a>
```
