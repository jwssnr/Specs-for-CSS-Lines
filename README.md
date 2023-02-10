# CSS Lines

### CSS Lines is a set of CSS properties that allow you to connect 2 or more elements with lines. The line ends will always remain anchored to their corresponding elements, adapting fluidly. They are a kind of pseudo-elements.


# Why?

1. Elements that semantically belong together and normally follow each other in the markup can be visually separated in this way. 
2. Multiple modals can be opened without losing the visual reference.
3. Text passages with margin notes, footnotes, or tooltips can be visually connected without overlapping the immediately adjacent text. 
4. Tabular content or lists can be broken up visually. This makes simple organizational charts possible..

2. For purely decorative purposes. Face it! 😁

# Example 1
**Turn a nested list into an Organigram.**

```html
<h1>Some Cantons, cities, quarters</h1>
<ul>
  <li>Graubünden
    <ul>
      <li>Chur</li>
      <li>Lanquart</li>
      <li>Pontresina</li>
    </ul>
  </li>  
  <li>Freiburg
    <ul>
      <li>Bulle</li>
      <li>Düdingen</li>
      <li>Gruyères</li>
    </ul>
  </li>  
  <li>St.Gallen
    <ul>
      <li>St.Gallen
        <ul>
          <li>St.Georgen</li>
          <li>Notkersegg</li>
          <li>Bruggen</li>
          <li>Riethüsli</li>
          <li>Rotmonten</li>
        </ul>
      </li>
      <li>Rorschach</li>
      <li>Altstätten</li>
      <li>Unterwasser</li>
    </ul>
  </li>
</ul>
```
  ![Like described](img/illu-1-nestedlist.png)

# Example 2

**Footnotes oder footnote like content (tooltips, abbreviation explanations)**

```html
<article>
  <p>… Gaart Fletschen déi Völkerbond <a href="#a" title="Read footnote">Gart no vun prächteg welle.</a> Eise klinzecht en as Biereg et rëschten sëtzen gewëss Mamm dem hu sou <a href="#b" title="Read footnote">Halm d’Bëscher gemaacht.</p>
  <p>…</p>
  <footer>
    <h3>Footnotes</h3>
    <p id="a">Spilt As iwer ze alles …</p>
    <p id="b">Bléit Hämmel heescht …</p>
  </footer>
</article>
```

![As described.](img/v2-footnotes.png)


# Usage — Set and join

Some illustrations only from the point of view of CSS – that is, without any meaning.

![Sketch of a CSS Line, connecting two elements.](img/v1-2-elements.png)

To get the result of this image, the usage would look like this:

```css
.a {
  set-lineanchor-name: a;
  set-lineanchor-position: calc(100% - 1rem) calc(100% - 1rem);
  set-lineanchor-z: -1;
  set-linestyle: 3px solid white rounded;
}
.b {
  join-lineanchor-name: a;
  join-lineanchor-position: center;
  join-lineanchor-z: 1; /* default */
}
```
##  Multiple lines from one referenze

![Like described.](img/v2-stern.png)

```css
.a {
  set-lineanchor-name: a;
  set-lineanchor-position: calc(100% - 1rem) 50%;
  set-lineanchor-z: -1;
  set-linestyle: 3px solid white rounded;
}
.b {
  join-lineanchor-name: a;
  join-lineanchor-position: 1rem 1rem;
}
```

## Different lines

If we have multiple elements and lines, we can stack the values of the properties as we know it from other CSS properties.

![Like described](img/v2-3-elements.png)

```css
.a {
  set-lineanchor-name: afront, aback;
  set-lineanchor-position: calc(100% - 1rem) 1rem, calc(100% - 1rem) 1rem;
  set-lineanchor-z: 1, -1;
  set-linestyle: 3px solid magenta squared, 3px solid white rounded;
}
.b {
  set-lineanchor-name: bfront;
  set-lineanchor-position: center;
  set-linestyle: 1px solid white rounded;

  join-lineanchor-name: aback;
  join-lineanchor-position: 1rem 1rem;
}
.c {
  join-lineanchor-name: afront, bfront;
  join-lineanchor-position: 1rem 1rem, center;
  join-lineanchor-z: -1, 1;
}
```
## Maybe we can go even further
![Like described.](img/v2-bezier.png)
```css
.a {
  set-lineanchor-name: 
    a, 
    b;
  set-lineanchor-position: 
    center, 
    50% calc(100% - 1rem);
  set-linestyle: 
    3px solid black rounded cubic-bezier(1,0,0,1), 
    1px solid white rounded cubic-bezier(.5,0,1,.5);
}
.b {
  fetch-lineanchor-name: 
    a, 
    b;
  fetch-lineanchor-position: 
    center, 
    50% calc(100% - 1rem);
  fetch-linestyle: 
    3px solid magenta, 
    3px solid white;
}
```

## Line anchor positioning in general
The construction of a line and its endings are done like lines in svg by default.

![As described.](img/line-anchor2.png)