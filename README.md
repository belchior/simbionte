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
    <$var type="object">
      <$var id="autor-name">Ned</$var>
      <$var id="autor-comment>The winter is coming</$var>
    </$var>
    <$var type="object>
      <$var id="autor-name" value="Hodor" />
      <$var id="autor-comment value="hodor, hodor" />
    </$var>
  </$var>
</$var>
```

### &lt;!-- usando variáveis --&gt;
```html
<$echo age />
<$echo person.name />
```

## &lt;!-- comentando código --&gt;
```html
<$--
<$var type="number" id="pi" value="3.14" />
<$var type="number" id="pi">3.14</$var>
-->
```

```html
<$function id="avatar" param="$url, $image, $name">
  <a href="$url"><img src="$image" alt="$name"><a>
</$function>

<$function avatar />
```

## &lt;!-- Iteradores --&gt;
```html
<$for cond="person of people">
  <span><$echo person.name /><span>
</$for>
```

## &lt;!-- Condicional --&gt;
```html
<$if cond="$title" id="test-title">
  <$then for="test-title"><h1><$echo title /><h1></$then>
  <$else for="test-title"><h1>No title<h1></$else>
</$if>
```

### &lt;!-- Variação de condicional --&gt;
```html
<$if cond="$title" id="test-title"></$if>
<$then for="test-title"><$echo title /></$then>
<$else for="test-title">No title</$else>
```
Declarações `then` e `else` dentro da declaração `if` teram precedência sobre as declarações que estiverem fora.


## &lt;!-- Importanto partes de código --&gt;
```html
<$import src="../path/to/file.htmls" />
```
