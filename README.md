# simbionte
> Consept of template engine to HTML
```html
<$var name="title" value="my title" type="string" />
<$var title="my title" />
<$var title />
```

```html
<$for cond="person of people">
  <span><$var  person.name /><span>
</$for>
```

```html
<$if cond="title" id="test-title">
  <h1>
    <$then for="test-title"><$var title /></$then>
    <$else for="test-title">No title</$else>
  <h1>
</$if>
```
