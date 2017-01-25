# simbionte
> Consept of template engine to HTML

```html
<!-- definição de variáveis -->


<!-- string -->
<$var type="string" id="title" value="my title" />
<$var type="string" id="title">my title</$var>

<!-- caso o tipo não for definido o padrão é string -->
<$var id="title" value="my title" />
<$var id="title">my title</$var>


<!-- number -->
<$var type="number" id="pi" value="3.14" />
<$var type="number" id="pi">3.14</$var>


<!-- array -->
<!-- tudo dentro de um array será considerado item -->
<$var type="array" id="myList">
  <$var type="number" value="42" />
  <$var>banana</$var>
</$var>

<!-- tudo referenciando um array será considerado item -->
<$var type="array" id="myList" />
<$var type="number" value="42" for="myList" />
<$var for="myList">banana</$var>


<!-- object -->
<$var type="object" id="person">
  <$var type="string" id="name">John</$var>
  <$var type="number" id="age">29</$var>
</$var>

<$var type="prop" for="person" id="name" value="John Snow"></$var>

<$function id="avatar">
  <a href="#"><img src="/avatar.png" alt="Profile avatar"><a>
</$function>

<$function avatar />


<$for cond="person of people">
  <span><$var  person.name /><span>
</$for>


<$if cond="title" id="test-title">
  <h1>
    <$then for="test-title"><$var title /></$then>
    <$else for="test-title">No title</$else>
  <h1>
</$if>


<$import src="../path/to/file.htmls" />
```
