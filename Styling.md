# Styling

### Global CSS Files:

Css files get applied at the root level to the whole project (Stu)

Pros:

- Works with preprocessors (Less, Sass)
- No webpack
- Easy Set up

Cons: 

- Possible collisions in the namespaces

### Style Sheet per component:

Each Component imports its own stylesheet

Pros: 

- No collisions
- works with preprocessors

Cons:

- More work to create files and imports
- More bloated file system

### Inline React styles:

styles are defined as javascript objects and added to the react elements

Pros:

- No collisions
- Easy to work with

Cons

- No preprocessor support
- Different Syntax
- No pseudo selectors (without a library, see CSS In JS below)
- Hard to transition existing project to

### CSS modules:

Scoped CSS files use Css module compile (webpack)

Pros:

- No collisions
- preprocessor Support
- Simple CSS

Cons:

- Need a special compiler

### CSS in JS Modules:

Inline react styles with a library (Styled components, Aphrodite, Radium, Material-ui styles)

Pros:

- No collisions
- Pseudo selector support

Cons:

- Needs external library
- May have different syntax
- No pre-processor support