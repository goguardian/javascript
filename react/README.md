# GoGuardian React/JSX Style Guide

*A mostly reasonable approach to React and JSX*

## Table of Contents

  1. [Basic Rules](#basic-rules)
  1. [Naming](#naming)
  1. [Declaration](#declaration)
  1. [Alignment](#alignment)
  1. [Quotes](#quotes)
  1. [Spacing](#spacing)
  1. [Props](#props)
  1. [Parentheses](#parentheses)
  1. [Tags](#tags)
  1. [Methods](#methods)
  1. [Ordering](#ordering)

## Basic Rules

  - Only include one React component per file.
  - Always use JSX syntax.
  - Do not use `React.createElement` unless you're initializing the app from a file that is not JSX.

## Class vs React.createClass

  - Use class extends React.Component unless you have a good reason to use mixins.

  ```javascript
  // ok
  const Student = React.createClass({
    render() {
      return <div />;
    }
  });

  // good
  class Student extends React.Component {
    render() {
      return <div />;
    }
  }
  ```

## Naming

  - **Extensions**: Use `.jsx` extension for React components.
  - **Filename**: Use camelCase for filenames. E.g., `classroomSession.jsx`.
  - **Reference Naming**: Use PascalCase for React components and camelCase for their instances:
    ```javascript
    // bad
    import classroomSession from './classroomSession';

    // good
    import ClassroomSession from './classroomSession';

    // bad
    const ClassroomSession = <ClassroomSession />;

    // good
    const classroomSession = <ClassroomSession />;
    ```

    **Component Naming**: Use the filename as the component name. For example, `ClassroomSession.jsx` should have a reference name of `ClassroomSession`. However, for root components of a directory, use `index.jsx` as the filename and use the directory name as the component name:
    ```javascript
    // bad
    import Footer from './Footer/Footer.jsx'

    // bad
    import Footer from './Footer/index.jsx'

    // good
    import Footer from './Footer'
    ```


## Declaration
  - Do not use displayName for naming components. Instead, name the component by reference.

    ```javascript
    // bad
    export default React.createClass({
      displayName: 'ClassroomSession',
      // stuff goes here
    });

    // good
    export default class ClassroomSession extends React.Component {
    }
    ```

## Alignment
  - Follow these alignment styles for JS syntax

    ```javascript
    // bad
    <Foo superLongParam="bar"
         anotherSuperLongParam="baz" />

    // good
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz" />

    // if props fit in one line then keep it on the same line
    <Foo bar="bar" />

    // children get indented normally
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz">
      <Spazz />
    </Foo>
    ```

## Quotes
  - Always use double quotes (`"`) for JSX attributes, but single quotes for all other JS. This keeps JSX as close to markup as possible.
    ```javascript
    // bad
    <Foo bar='bar' />

    // good
    <Foo bar="bar" />

    // bad
    <Foo style={{ left: "20px" }} />

    // good
    <Foo style={{ left: '20px' }} />
    ```

## Spacing
  - Always include a single space in your self-closing tag.
    ```javascript
    // bad
    <Foo/>

    // very bad
    <Foo                 />

    // bad
    <Foo
     />

    // good
    <Foo />
    ```

## Props
  - Always use camelCase for prop names.
    ```javascript
    // bad
    <Foo
      UserName="hello"
      phone_number={12345678} />

    // good
    <Foo
      userName="hello"
      phoneNumber={12345678} />
    ```

## Parentheses
  - Wrap JSX tags in parentheses when they span more than one line:
    ```javascript
    /// bad
    render() {
      return <MyComponent className="long body" foo="bar">
               <MyChild />
             </MyComponent>;
    }

    // good
    render() {
      return (
        <MyComponent className="long body" foo="bar">
          <MyChild />
        </MyComponent>
      );
    }

    // good, when single line
    render() {
      const body = <div>hello</div>;
      return <MyComponent>{body}</MyComponent>;
    }
    ```

## Tags
  - Always self-close tags that have no children.
    ```javascript
    // bad
    <Foo className="stuff"></Foo>

    // good
    <Foo className="stuff" />
    ```

  - If your component has multi-line properties, close its tag on the last property. Avoid closing tags on their own line.
    ```javascript
    // bad
    <Foo
      bar="bar"
      baz="baz"
    />

    // good
    <Foo
      bar="bar"
      baz="baz" />
    ```

## Methods
  - Use object method shorthand for internal methods of a React component.
  ```javascript
  // don't
  const Student = React.createClass({
    render: function() {
      return <div />
    }
  });

  // do
  const Student = React.createClass({
    render() {
      return <div />
    }
  });
  ```

  - Do not use underscore prefix for internal methods of a React component.
    ```javascript
    // bad
    React.createClass({
      _onClickSubmit() {
        // do stuff
      }

      // other stuff
    });

    // good
    class Student extends React.createClass({
      onClickSubmit() {
        // do stuff
      }

      // other stuff
    });
    ```

## Ordering

  - Ordering for React.createClass:

  1. displayName
  1. propTypes
  1. contextTypes
  1. childContextTypes
  1. mixins
  1. statics
  1. defaultProps
  1. getDefaultProps
  1. getInitialState
  1. getChildContext
  1. componentWillMount
  1. componentDidMount
  1. componentWillReceiveProps
  1. shouldComponentUpdate
  1. componentWillUpdate
  1. componentDidUpdate
  1. componentWillUnmount
  1. *getter methods for render* like getSelectReason() or getFooterContent()
  1. *clickHandlers or eventHandlers* like onClickSubmit() or onChangeDescription()
  1. *Optional render methods* like renderNavigation() or renderProfilePicture()
  1. render

**[⬆ back to top](#table-of-contents)**
