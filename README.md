# REACT-MASONRY-LAYOUT

## Description

This repository is a Software of Application with React,NodeJS,SASS,etc

## Installation

Using NodeJS, React preferably.

## Plugins

AOS, React Transitions Group, React Reveal,etc


## Usage

```html
$ git clone https://github.com/DanielArturoAlejoAlvarez/react-masonry-layout[NAME APP]

$ npm install

$ yarn install

```

Follow the following steps and you're good to go! Important:

![alt text](https://i1.wp.com/reactscript.com/wp-content/uploads/2016/11/React-Masonry-Infinite-Scroller.png?ssl=1)

## Coding

### Views
```js
...
const App = () => {
  const [cols, setCols] = useState(3);

  const [CSSTransitions, setCSSTransitions] = useState("");

  useEffect(() => {
    setCSSTransitions("ball");
  }, [cols]);

  return (
    <main className={CSSTransitions}>
      <Fade isOpen={true}>
        <Masonry cols={cols} gutter={2} />
      </Fade>
    </main>
  );
};
...
```

### Components
```js
...
export const Masonry = (props) => {
  const gutter = {
    gridGap: `${props.gutter}rem`,
  };

  const [data, setData] = useState([]);
  const [columnElements] = useState([]);
  const [gallery, setGallery] = useState("");

  const [values] = useState({
    columns: props.cols,
  });

  useEffect(() => {
    setData(images.gallery);
    setGallery(`gallery masonry-layout columns-${values.columns}`);
    masonryLayout(
      document.getElementById("gallery"),
      document.querySelectorAll(".gallery-item"),
      values.columns,
      columnElements
    );
  }, [data, values, columnElements]);

  return (
    <div className={gallery} style={gutter} id="gallery">
      {!data ? (
        <div>Loading...</div>
      ) : (
        data.map((item, index) => (
          <Item
            id={item.id}
            url_image={item.url_image}
            caption={item.caption}
            key={index}
          />
        ))
      )}
    </div>
  );
};
...
```

### Helpers
```js
...
export const masonryLayout = (container, elements, cols, columnElements) => {
  for (let i = 1; i <= cols; i++) {
    let column = document.createElement("div");
    column.classList.add("masonry-column", `column-${i}`);
    container.appendChild(column);
    columnElements.push(column);
  }

  for (let m = 0; m < Math.ceil(elements.length / cols); m++) {
    for (let n = 0; n < cols; n++) {
      let item = elements[m * cols + n];
      columnElements[n].appendChild(item);
      item.classList.add("masonry-item");
    }
  }
};
...
```

### SASS
```scss
...
.masonry-layout {
  --columns: 1;
  --gap: 2rem;
  $columns: 8;


  display: grid;
  grid-template-columns: repeat(var(--columns), 1fr);
  grid-gap: var(--gap);

  .masonry-item {
    margin-bottom: var(--gap);
  }

  @for $i from 1 through $columns {
    &.columns-#{$i} {
      --columns: #{$i}
    }
  }
}
...
```




## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/DanielArturoAlejoAlvarez/react-masonry-layout. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

```

```
