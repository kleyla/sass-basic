# SASS
Instalar ruby
Instalar sass con:
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

