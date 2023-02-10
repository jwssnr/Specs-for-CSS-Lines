# CSS Lines

### CSS Lines is a set of CSS properties that allow you to connect 2 or more elements with lines. The line ends will always remain anchored to their corresponding elements, adapting fluidly. They are a kind of pseudo-elements.


# Why?

1. Elements that semantically belong together and usually follow each other in the markup can be visually separated in this way. This is helpful if, for example, several modals are to be opened. Or when text passages with margin notes or footnotes are to be visually connected. Or when popups in texts should not overlay the immediately adjacent text. Or when tabular content is to be visually broken up. Or for organizational charts and simple infographics that would otherwise require SVG.

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
      <li>Atstätten</li>
      <li>Unterwasser</li>
    </ul>
  </li>
</ul>
```
  ![Like described](img/illu-1-nestedlist.png)

---

Now some illustrations only from the point of view of CSS – that is, without any meaning.

# Usage — Set and fetch

![Sketch of a CSS Line, connecting two elements.](img/v1-2-elements.png)

To get the result of this image, the usage would look like this:

```css
.a {
  set-line-name: ab;
  set-line-anchor: calc(100% - 1rem) calc(100% - 1rem);
  set-line-z: -1;
  set-line-style: 3px solid white rounded;
}
.b {
  fetch-line-name: ab;
  fetch-line-z: 1; /* default */
  fetch-line-anchor: center;
}
```
##  Multiple lines from one referenze

![Like described.](img/v2-stern.png)

```css
.a {
  set-line-name: ab;
  set-line-anchor: calc(100% - 1rem) 50%;
  set-line-z: -1;
  set-line-style: 3px solid white rounded;
}
.b {
  fetch-line-name: ab;
  fetch-line-anchor: 1rem 1rem;
}
```

##  Different lines

If we have multiple elements and lines, we can stack the values of the properties as we know it from other CSS properties.

![Like described](img/v2-3-elements.png)

```css
.a {
  set-line-name: afront, aback;
  set-line-anchor: calc(100% - 1rem) 1rem, calc(100% - 1rem) 1rem;
  set-line-z: 1, -1;
  set-line-style: 3px solid magenta squared, 3px solid white rounded;
}
.b {
  fetch-line-name: aback;
  fetch-line-anchor: 1rem 1rem;
  set-line-style: 1px solid white rounded;
  set-line-name: bfront;
  set-line-anchor: center;
}
.c {
  fetch-line-name: afront, bfront;
  fetch-line-anchor: 1rem 1rem, center;
  fetch-line-z: -1, 1;
}
```
# Maybe we can go even further
![Like described.](img/v2-bezier.png)
```css
.a {
  set-line-name: 
    a, 
    b;
  set-line-anchor: 
    center, 
    50% calc(100% - 1rem);
  set-line-style: 
    3px solid black rounded cubic-bezier(1,0,0,1), 
    1px solid white rounded cubic-bezier(.5,0,1,.5);
}
.b {
  fetch-line-name: 
    a, 
    b;
  fetch-line-anchor: 
    center, 
    50% calc(100% - 1rem);
  fetch-line-style: 
    3px solid magenta, 
    3px solid white;
}
```

# Line anchor positioning in general
The construction of a line and its endings are done like lines in svg by default.

![As described.](img/line-anchor2.png)