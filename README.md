# Best Practices for React or React Native Projects
This is a list of best practices and nice to know things for react or react native project.

> **Note**: These are all opinionated practices and may change over time. So make sure to watch this repo.

## :book: Table of Contents

  * [File and Folder Structure](#folder-and-files)
    * [Type Based](#folder-type-based)
    * [Feature Based](#folder-feature-based)
  * [Necessary Libraries](#required-libs)
    * [Axios](#libs-axios)
    * [ESLint](#libs-eslint)
    * [Moment](#libs-moment)
    * [React Router Dom](#libs-router)
    * [Redux](#libs-redux)
    * [Third-Party Libs](#libs-redux)
  * [Code Style](#code-style)
  * [Hooks](#hooks)
  * [Git](#git)
  * [Support Multi-lang](#multi-lang)
  * [Accessibility](#accessibility)
  * [Components](#components)
    * [Naming](#naming)
    * [Functional Components](#functional-components)
    * [Class Components](#class-components)
    * [Higher-Order Components](#class-hoc)
  * [Styling](#component-stylings)
    * [SCSS](#styling-scss)
    * [styled-components](#styling-styled-component)
    * [Inline Styling](#styling-inline)
  * [Images](#assets)
  * [Style Libraries](#style-libs)
  * [Memory Leak Handling](#memory-leaks)
  * [Server Side Rendering](#ssr)
  * [Testing](#testing)
  * [Build and Deployment](#building)


## File and Folder Structure
<a name="folder-and-files"></a>
Based on what [React](https://reactjs.org/docs/faq-structure.html) says, we have two main ways of structuring files and folders.

  <a name="folder-type-based"></a>
  - [By File Type](#folder-type-based)


  Put your components in `components` folder. Put your helper functions inside `helpers` folder. Put your redux files inside `redux` or `app` folder and so on.

  This way you seperate files by their type.

  *Example:*
  ```javascript
  /**
    src/
    |   App/
    |   |   Actions/
    |   |   |   cartActions.js
    |   |   Constants/
    |   |   |   cartConsts.js
    |   |   Reducers/
    |   |   |   cartReducers.js
    |   |   Store/
    |   |   |   cartStore.js
    |   |   ...
    |   |
    |   Helpers/
    |   |   cartHelpers.js
    |   |
    |   Components/
    |   |   cartHeader.js
    |   |   cartItem.js
    |   |   cartFooter.js
    |   |
    |     ...
  */
  ```


  <a name="folder-feature-based"></a>
  - [By Route or Feature](#folder-feature-based)


  Create folder for each of your pages inside the `pages` folder, then put whatever thats related to that feature inside that folder. Imagine you have a `Cart` folder then you will have all of its components inside `Cart/components` folder. The redux files goes into `Cart/redux` folder and related helpers goes into `Cart/helpers` folder.

  This way you seperate files by the application features.

  *Example:*
  ```javascript
  /**
    src/
    |   Pages/
    |   |   Pages/
    |   |   |   Cart/
    |   |   |   |   Components/
    |   |   |   |   |   cartItem.js
    |   |   |   |   |   cartHeader.js
    |   |   |   |   |   cartFooter.js
    |   |   |   |   Helpers/
    |   |   |   |   |   index.js <- cartHelpers.js in previous example
    |   |   |   |   Redux/
    |   |   |   |   |   cartActions.js
    |   |   |   |   |   cartConsts.js
    |   |   |   |   |   cartReducers.js
    |   |   |   |   |   cartStore.js
    |   |   |   |   |   index.js <- Here you import all other things (reducers, actions, etc.)
    |   |   |   |   Cart.js
    |   |   |   |   index.js
    |   |   |   ...
    |   |   |   Product/
    |   |   |   |   ... <- Like Cart
    |     ...
  */
  ```


:heavy_exclamation_mark: **My Advice** Althouth it's more about what you want to do but I found the [feature based](#folder-feature-based) more useful.

## :white_medium_square: Todos:
- [x] ~~Create table of contents~~
- [ ] Code snippets
- [ ] Code screenshots