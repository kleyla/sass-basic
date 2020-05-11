# SASS
<p>Instalar ruby.</p>
<p>Instalar sass con:</p>
```bash
    gem install sass
```
En el folder assets tener un folder para css y otro para scss

```bash
    cd assets/
    sass --watch scss/archivo.scss:css/archivo.css
```
Este comando vigilara los cambios que vamos haciendo en la hoja sass y genera el archivo css.

## Anidacion de codigo
Codigo en css:
```css
    header {
        color: #fff;
        background: #cc6699;
        padding: 10rem 0;
        text-align: center;
        position: relative;
        z-index: 1;
        overflow: hidden;
    }
    header h1 {
        font-size: 3rem;
        margin: 0 0 1rem;
    }
    header h2 {
        font-weight: 300;
        font-size: 1.5rem;
        margin: 0 0 1rem;
    }
```
Codigo en SCSS:
```scss
    header {
        color: #fff;
        background: #cc6699;
        padding: 10rem 0;
        text-align: center;
        position: relative;
        z-index: 1;
        overflow: hidden;

        h1 {
            font-size: 3rem;
            margin: 0 0 1rem;
        }
        h2 {
            font-weight: 300;
            font-size: 1.5rem;
            margin: 0 0 1rem;
        }
    }
```
Con clases (css):
```CSS
    .btn {
        display: inline-block;
        margin: 1rem 0;
        color: #fff;
        font-weight: 500;
        font-size: 1.3rem;
        background: #cc6699;
        letter-spacing: 0.02rem;
        border: none;
        border-radius: 5px;
        padding: 0.8rem 1rem 0.9rem;
        text-shadow: 0 1px rgba(0, 0, 0, 0.3);
        box-shadow: 0 0 2px rgba(0, 0, 0, 0.2);
    }
    .btn:hover {
        background: #864566;
        color: #fff;
    }
    .btn:focus, .btn:active, .btn:focus:active {
        background: #006eb4;
        border-color: #006eb4;
        box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.5) inset;
    }
```
En SCSS remplazamos la clase padre por "&"
```SCSS
.btn {
  display: inline-block;
  margin: 1rem 0;
  color: #fff;
  font-weight: 500;
  font-size: 1.3rem;
  background: #cc6699;
  letter-spacing: 0.02rem;
  border: none;
  border-radius: 5px;
  padding: 0.8rem 1rem 0.9rem;
  text-shadow: 0 1px rgba(0, 0, 0, 0.3);
  box-shadow: 0 0 2px rgba(0, 0, 0, 0.2);

  &:hover {
    background: #864566;
    color: #fff;
  }
  &:focus,
  &:active,
  &:focus:active {
    background: #006eb4;
    border-color: #006eb4;
    box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.5) inset;
  }
}
```
Comentarios en SCSS:
```SCSS
    // una linea
    /* multi
     lineas */
```
## Variables
```SCSS
$color-rosa: #cc6699;
```

## Operaciones matematicas
```SCSS
$todo: 100%;
$ventana: 30%;
$box: $todo - $ventana;
```

## Mixins
En CSS hay redundancia en algunas lineas de codigo, mixin nos permite factorizar e incluir donde sea necesario.
```CSS
section > h1 {
    margin: 0 0 20px 0;
    font-family: Georgia;
    font-size: 20px;
    font-weight: bold;
    text-transform: uppercase;
    color: #333;
}
section > h2 {
    margin: 0 0 20px 0;
    font-family: Georgia;
    font-size: 20px;
    font-weight: bold;
    text-transform: uppercase;
    color: #666;
}
```
A SCSS:
```SCSS
@mixin titulo{
    margin: 0 0 20px 0;
    font-family: Georgia;
    font-size: 20px;
    font-weight: bold;
    text-transform: uppercase;
}
section > h1 {
    @include titulo;
    color: #333;
}
section > h2 {
    @include titulo;
    color: #666;
}
```
Esto tambien nos permite enviar parametros, parametros por default:
```SCSS
@mixin titulo($fsize, $fweight: bold) {
    margin: 0 0 20px 0;
    font-family: Georgia;
    font-size: $fsize;
    font-weight: $fweight;
    text-transform: uppercase;
}
section > h1 {
    @include titulo(22px);
    color: #333;
}
section > h2 {
    @include titulo(18px, 600);
    color: #666;
}
```

```SCSS
@mixin shadow($x, $y, $blur, $color) {
    --webkit-box-shadow: $x $y $blur $color;
    -moz-box-shadow: $x $y $blur $color;
    box-shadow: $x $y $blur $color;
}

#caja1 {
    @include shadow(1px, 2px, 5px, rgba(0,0,0,0.6) )
}
```
## Extend
```scss
$color-alerta: #67e24f;
$color-error: #b23f24;
$color-acceso: #46b6ea;

@mixin sombras {
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.5);
  -webkit-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.5);
  -moz-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.5);
}
@mixin bordes {
  border-radius: 10px;
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
}
.alerta {
  padding: 15px;
  font-size: 1.2rem;
  font-weight: normal;
  text-transform: uppercase;
  line-height: 1;
  margin-bottom: 5px;
  letter-spacing: 3px;
  text-align: center;
  color: #fff;
  background: $color-alerta;
  @include sombras();
  @include bordes();
}
.error {
  @extend .alerta;
  background: $color-error;
  font-size: 10px;
}
.acceso {
  @extend .alerta;
  @extend .error;
  background: $color-acceso;
}
```
## Placehoder
Estilos fantasma
```scss
%button {
  padding: 10px;
  color: #fff;
  background: blue;
  border-radius: 6px;
  display: inline-block;
}
.cancelar {
  @extend %button;
  background: $color-error;
}
.enviar {
  @extend %button;
  background: $color-acceso;
}
```
## Partials
Archivos .scss que son incluidos en el .scss principal. Deben ser llamados _nombre.scss.
<p>Por lo general existen estos archivos: _reset.scss _mixin.scss _variables.scss</p>
```scss
@import "reset";
@import "mixins";
@import "variables";
```