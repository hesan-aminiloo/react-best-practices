# Best Practices for React or React Native Projects
This is a list of best practices and nice to know things for react or react native project.

> **Note**: These are all opinionated practices and may change over time. So make sure to watch this repo.

## :book: Table of Contents

  * [Tools](#required-tools)
  * [Noticeable Libraries](#required-libs)
  * [File and Folder Structure](#folder-and-files)
    * [Type Based](#folder-type-based)
    * [Feature Based](#folder-feature-based)
  * [Components](#components)
    * [Naming](#naming)
    * [Functional Components](#functional-components)
    * [Class Components](#class-components)
    * [Higher-Order Components](#class-hoc)
  * [Code Style](#code-style)
  * [Hooks](#hooks)
  * [Git](#git)
  * [Support Multi-lang](#multi-lang)
  * [Accessibility](#accessibility)
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


## Tools
<a name="required-tools"></a>
Here's a list of tools and extensions that are useful when you're working on a React project.

:pencil: **FEEL FREE TO CREATE A PR AND COMPLETE THIS LIST**

  - [React Developer Tools](https://reactjs.org/blog/2019/08/15/new-react-devtools.html)
  > Used to debug and inspect your whole react application in the browser.
  - [**VSCode extensions**](https://code.visualstudio.com/)
    - [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
    > This extenstion is used to highlight linter issues in your code editor.
    - [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
    > Autocomplete path addresses
    - [Turbo Console Log](https://marketplace.visualstudio.com/items?itemName=ChakrounAnas.turbo-console-log)
    > This is one of my favorites! Put console logs in your code with no effort.
    - [vscode-styled-components](https://marketplace.visualstudio.com/items?itemName=jpoissonnier.vscode-styled-components)
    > When your using `styled-components` with react, this extention helps you to highlight scss/css syntax.
    - [Gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
    > Gitlens is a good tool to work with git in your project.
    - [Bookmarks](https://marketplace.visualstudio.com/items?itemName=alefragnani.Bookmarks)
    > Bookmark your codes and jump into them. Perfect tool for debugging.
    - [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
    > Colorize the brackets and parentheses.
    - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
    > Start a live server locally with one click.

## Noticeable Libraries
<a name="required-libs"></a>
There are hundreds of useful libraries for javascript and react. I didn't want to list all these libs, I just want to list the useful ones that every project needs them.

:pencil: **FEEL FREE TO CREATE A PR AND COMPLETE THIS LIST**

| Lib                                                                               | Description                                  | install                     |
|-----------------------------------------------------------------------------------|----------------------------------------------|-----------------------------|
| [Axios](https://github.com/axios/axios)                                           | Communicate to server                        | `yarn add axios`            |
| [React Router Dom](https://reacttraining.com/react-router/web/guides/quick-start) | Navigation and routing for React             | `yarn add react-router-dom` |
| [ESLint](https://thomlom.dev/setup-eslint-prettier-react/)                        | Lint your code to have a better handwriting. | `yarn add eslint`           |
| [Moment](https://momentjs.com/)                                                   | Best tool to work with time.                 | `yarn add moment`           |
| [Redux](https://redux.js.org/)                                                    | State management.                            | `yarn add redux`            |
| [React Redux](https://react-redux.js.org/)                                        | Official React bindings for Redux            | `yarn add react-redux`      |



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
    |   |   Cart/
    |   |   |   Components/
    |   |   |   |   cartItem.js
    |   |   |   |   cartHeader.js
    |   |   |   |   cartFooter.js
    |   |   |   Helpers/
    |   |   |   |   index.js <- cartHelpers.js in previous example
    |   |   |   Redux/
    |   |   |   |   cartActions.js
    |   |   |   |   cartConsts.js
    |   |   |   |   cartReducers.js
    |   |   |   |   cartStore.js
    |   |   |   |   index.js <- Here you import all other things (reducers, actions, etc.)
    |   |   |   Cart.js
    |   |   |   index.js
    |   |   |   ...
    |   |   Product/
    |   |   |   ... <- Like Cart
    |   |   ... (Other pages)
    ...
  */
  ```


:heavy_exclamation_mark: **My Advice:** Althouth it's more about what you want to do but I found the [feature based](#folder-feature-based) more useful.


## Components
<a name="components"></a>

  [Create more components](https://reactjs.org/blog/2015/12/18/react-components-elements-and-instances.html#summary)
  ```javascript
  import React from 'react';

  const Button = () => (
    <button>
      You can click me!
    </button>
  );

  // or

  class Button extends React.Component {
    render(){
      return (
        <button>
          Or click me!
        </button>
      );
    }
  }
  ```

  **WHY?**  It's cheap to create a new component in react as they are plain javascript objects. Creating more components gives you the ability to reuse your logic and codes easier and avoid repetetive code in your application. It also makes it easier to change or modify your code. Imagine you want to change the color of all buttons in your application, the only place to change is one component instead of every button in your application.

  **NOTE:** Creating components in react is cheap, so try to use them a lot.
  <br/>
  <br/>

  [Use Functional Components](https://medium.com/@Zwenza/functional-vs-class-components-in-react-231e3fbd7108)
  ```javascript
  import React from 'react';

  /**
   * Meh... not bad
   */
  class Navigation extends React.Component {
    constructor(props) {
      super(props);
    }

    render(){
      const { items } = this.props;

      return (
        <ul>
          {
            items.map(item => (
              <li>
                <a href={item.href}>{item.label}</a>
              </li>
            ))
          }
        </ul>
      );
    }
  }


  /**
   * So Much Better!
   */
  const Navigation = ({ items }) => (
    <ul>
      {
        items.map(item => (
          <li>
            <a href={item.href}>{item.label}</a>
          </li>
        ))
      }
    <ul>
  );

  ```

  **WHY?**  Functional components are **easy to read** and understand. They are **more testable** since they are just a simple function and even if you want them to have state or lifecycles there would be no problem cause we have react hooks now! Also they have a slightly [better performance](https://reactjs.org/blog/2015/10/07/react-v0.14.html#stateless-functional-components) comparing to class-components.

  **NOTE:** With functional components you'll end up having **Less Code**, **More Testable Application** and **Easier to Read Logic**.
  <br/>
  <br/>

  [Make reusable components](https://blog.bitsrc.io/reusable-components-in-react-a-practical-guide-ec15a81a4d71)
  [Naming components](https://medium.com/@wittydeveloper/react-components-naming-convention-%EF%B8%8F-b50303551505)

## :white_medium_square: Todos:
- [x] ~~Create table of contents~~
- [ ] Code snippets
- [ ] Code screenshots