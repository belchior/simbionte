# Simbionte
> Concept of template engine for HTML

## &lt;!-- definição de variáveis --&gt;

### &lt;!-- string --&gt;
```html
<$var type="string" id="title" value="my title" />
<$var type="string" id="title">my title</$var>
```

##### &lt;!-- caso o tipo não seja definido o padrão será string --&gt;
```html
<$var id="title" value="my title" />
<$var id="title">my title</$var>
```

### &lt;!-- number --&gt;
```html
<$var type="number" id="pi" value="3.14" />
<$var type="number" id="pi">3.14</$var>
```

### &lt;!-- array --&gt;
##### &lt;!-- tudo dentro de um array será considerado item --&gt;
```html
<$var type="array" id="myList">
  <$var type="number" value="42" />
  <$var>banana</$var>
</$var>
```

##### &lt;!-- tudo referenciando um array será considerado item --&gt;
```html
<$var type="array" id="myList" />
<$var type="number" value="42" for="myList" />
<$var for="myList">banana</$var>
```

### &lt;!-- object --&gt;
```html
<$var type="object" id="person">
  <$var type="string" id="name">John</$var>
  <$var type="number" id="age">29</$var>
</$var>
```

### &lt;!-- estrutura de dados complexas --&gt;
```html
<$var type="object" id="article">
  <$var type="string" id="title">About next season of GoT</$var>
  <$var type="number" id="comments-count">2</$var>
  <$var type="array" id="comments">
    <$var id="comment>
      <$var id="autor-name" value="Ned" />
      <$var id="autor-comment>The winter is coming</$var>
    </$var>
    <$var id="comment>
      <$var id="autor-name" value="Hodor" />
      <$var id="autor-comment>hodor, hodor</$var>
    </$var>
  </$var>
</$var>
```

### &lt;!-- usando variáveis --&gt;
```html
<$echo age />
<$echo person.name />
```

##### &lt;!-- comentando código --&gt;
```html
<$--
<$var type="number" id="pi" value="3.14" />
<$var type="number" id="pi">3.14</$var>
-->;
```

```html
<$function id="avatar" param="$url, $image, $name">
  <a href="$url"><img src="$image" alt="$name"><a>
</$function>

<$function avatar />
```

```html
<$for cond="person of people">
  <span><$var person.name /><span>
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

```html
<$import src="../path/to/file.htmls" />
```
