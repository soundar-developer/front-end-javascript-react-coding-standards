# UI Coding Standards

## React

### Project Folder Structure

- Top level folders should be in lower case with hyphens ( src, config, fonts, images, redux, types, and so on.,)
- Components/Pages level folders should be in Title case
- Keep test files inside the component/page folder
    For example `Home/__test__`

### Components Folder Structure

- Create Domain specific components
- Separate the logic & view of a component and add into two separate files.

> For example, Learner.logic.tsx & Learner.view.tsx

1. Basic Template

    ```Text
        \LearnerProfile
            \__test__
                LearnerProfile.spec.tsx
            LearnerProfile.logic.tsx
            LearnerProfile.view.tsx
            Index.tsx
    ```

1. Use the below template for nested components

    ```Text
        LearnerProfile
            components
                LearnerIDCard
                    __test__
                        LearnerIDCard.spec.tsx
                    LearnerIDCard.logic.tsx
                    LearnerIDCard.view.tsx
                    Index.tsx
            __test__
                LearnerProfile.spec.tsx
            LearnerProfile.logic.tsx
            LearnerProfile.view.tsx
            Index.tsx
    ```

1. Use the Below template for component with redux

    ```Text
        LearnerProfile
            __test__
                LearnerProfile.spec.tsx
            redux
                __test__
                    Slices.spec.ts
                    Reducer.spec.ts
                Slices.ts
                Reducer.ts
                Index.ts
            LearnerProfile.logic.tsx
            LearnerProfile.view.tsx
            Index.tsx
    ```

1. Use below template for component with nested component and redux

    ```Text
        LearnerProfile
            components
                LearnerIDCard
                    __test__
                        LearnerIDCard.spec.tsx
                    LearnerIDCard.logic.tsx
                    LearnerIDCard.view.tsx
                    Index.tsx
            __test__
                LearnerProfile.spec.tsx
            redux
                __test__
                    Slices.spec.ts
                    Reducer.spec.ts
                Slices.ts
                Reducer.ts
                Index.ts
            LearnerProfile.logic.tsx
            LearnerProfile.view.tsx
            Index.tsx
    ```

### Naming

1. Type script files

    - Use .tsx extension for typescript React components files
    - Use PascalCase for typescript filenames

    ```Text
        // bad
        profileMenu.tsx

        // good
        ProfileMenu.tsx
    ```

1. __eslint: react/jsx-pascal-case__

    - Use PascalCase for React components

    ```Typescript
        // bad
        import profileMenu from './ProfileMenu';

        // good
        import ProfileMenu from './ProfileMenu';
    ```

1. __eslint: react/jsx-pascal-case__

    - camelCase for their Component References

    ```Typescript
        // bad
        const ProfileMenu = <ProfileMenu />;

        // good
        const profileMenu = <ProfileMenu />;
    ```

### Spacing

1. __eslint: no-multi-spaces, react/jsx-tag-spacing__

    - Include single space in closing component or tag

    ```Typescript
        // bad
        <Header/>

        // very bad
        <Header            />

        // bad
        <Header
        />

        // good
        <Header />
    ```

1. __eslint: react/jsx-curly-spacing__

    - Do not pad JSX curly braces with spaces

    ```Typescript
        // bad
        <Header logo={ logo } />

        // good
        <Header logo={logo} />
    ```

### Quotes

1. __eslint: jsx-quotes__

    - Use double quotes (") for JSX attributes

    ```Typescript
        // bad
        <Header logo='logo' />

        // good
        <Header logo="logo" />
    ```

### Alignment

1. __eslint: react/jsx-closing-bracket-location react/jsx-closing-tag-location__

    - If no prop in component or tag

    ```Typescript
        // bad
        <Header/>

        // good
        <Header />
    ```

1. __eslint: react/jsx-closing-bracket-location react/jsx-closing-tag-location__

    - If only one prop in component or tag

    ```Typescript
        // bad
        <Header 
            logo="pic" 
        />

        // good
        <Header logo="pic" />
    ```

1. __eslint: react/jsx-closing-bracket-location react/jsx-closing-tag-location__

    - If more than one prop in component or tag

    ```Typescript
        // bad 
        <Header logo="pic" profile="icon" />

        // bad
        <Header 
            logo="pic" 
            profile="icon" />

        // good
        <Header 
            logo="pic" 
            profile="icon" 
        />
    ```

1. __eslint: react/jsx-closing-bracket-location react/jsx-closing-tag-location__

    - If child component in component or tag

    ```Typescript
        // bad
        <Header
            logo="pic"
            profile="icon">
            <Title />
        </Header>

        // bad
        <Header
            logo="pic"
            profile="icon"
            >
            <Title />
        </Header>

        // good
        <Header
            logo="pic"
            profile="icon"
        >
            <Title />
        </Header>
    ```

### Props

1. Use camelCase for prop names

    ```Typescript
        // bad
        <Contact
            UserName="John"
            phone_number={627265378}
        />

        // good
        <Contact
            userName="Jack"
            phoneNumber={735382927}
        />
    ```

1. __eslint: react/jsx-boolean-value__

    - Omit the value of the prop when it is explicitly __true__

    ```Typescript
        // bad
        <Profile hidden={true} />

        // good
        <Profile hidden />
    ```

1. __eslint: jsx-a11y/alt-text__

    - Always include an alt prop on `<img>` tags

    ```Typescript
        // bad
        <img src="hello.jpg" />

        // good
        <img 
            src="hello.jpg" 
            alt="hello-loading" 
        />
    ```

### Tags

1. __eslint: react/self-closing-comp__

    - self-close tags that have no children

    ```Typescript
        // bad
        <Header logo="logo"></Header>

        // good
        <Header logo="logo" />
    ```

1. __eslint: react/jsx-closing-bracket-location__

    - If component has multi-line properties then close its tag on a new line

    ```Typescript
        // bad 
        <Header logo="pic" profile="icon" />

        // bad
        <Header 
            logo="pic" 
            profile="icon" />

        // good
        <Header 
            logo="pic" 
            profile="icon" 
        />
    ```

### Enable Eslint Rules

- __eslint: react/jsx-pascal-case__
- __eslint: no-multi-spaces, react/jsx-tag-spacing__
- __eslint: react/jsx-curly-spacing__
- __eslint: react/jsx-curly-spacing__
- __eslint: jsx-quotes__
- __eslint: react/jsx-closing-bracket-location react/jsx-closing-tag-location__
- __eslint: react/jsx-boolean-value__
- __eslint: jsx-a11y/alt-text__
- __eslint: react/self-closing-comp__
- __eslint: react/jsx-closing-bracket-location__

## File Template

### Home.view.tsx

1. __If no props then use below view template__

    - import statements on start of the file
    - Use arrow function with JSX.Element as return type
    - Store the arrow function in const reference
    - Use View as suffix for const reference name
    - export default statements on end of the file

    ```Typescript
        import "./Style.scss"

        const HomeView: () => JSX.Element = () => (
            <div 
                data-testid="tid-view-home"
                className="elr-home"
            >
                <h1>Home View Template </h1>
            </div>
        ) 

        export default HomeView;
    ```

1. __If 1 or more props then use below view template__

    - import statements on start of the file
    - Create interface to define props after import statements
    - Use arrow function with JSX.Element as return type
    - Store the arrow function in const reference
    - Use View as suffix for const reference name
    - create code block and destructure the props object in first line of the arrrow function
    - export default statements on end of the file

    Example 1

    ```Typescript
        import "./Style.scss"

        interface IHomeViewProps {
            title: string
        }

        const HomeView: (props: IHomeViewProps) => JSX.Element = (props: IHomeViewProps) => {
            // If you want to access the state or methods then get that as props from Logic file
            const {title} = props

            // Don't write logics like useState, useEffect, methods here
            return (
                <div 
                    data-testid="tid-home"
                    className="elr-home"
                >
                    <h1>{title} </h1>
                </div>
            )
        }

        export default HomeView;
    ```

    Example 2

    ```Typescript
        import "./Style.scss"

        interface IHomeViewProps {
            title: string
            subTitle: string
            paragraph: string
        }

        const HomeView: (props: IHomeViewProps) => JSX.Element = (props: IHomeViewProps) => {
            // If you want to access the state or methods then get that as props from Logic file
            const {title, subTitle, paragraph} = props

            // Don't write logics like useState, useEffect, methods here
            return (
                <div 
                    data-testid="tid-home"
                    className="elr-home"
                >
                    <h1>{title} </h1>
                    <h2>{subtitle} </h2>
                    <p>{paragraph} </p>
                </div>
            )
        }

        export default HomeView;
    ```

### Home.logic.tsx

1. __If no props then use below logic template__

    - import statements on start of the file
    - Use arrow function with React.FC as return type
    - Store the arrow function in const reference
    - Don't use Logic as suffix for const reference name
    - export default statements on end of the file

    Example 1

    ```Typescript
        import React from "react";
        import HomeView from "./Home.view";

        const Home: React.FC = () => <HomeView />;

        export default Home;
    ```

    Example 2

    ```Typescript
        import React from "react";
        import HomeView from "./Home.view";

        const Home: React.FC = () => {
            // write logics like useState, useEffect, methods here

            // If you want to access the state or methods then pass that as props to View file
            return <HomeView />
        }

        export default Home;
    ```

1. __If one or two props then use below logic template__

    - import statements on start of the file
    - Use arrow function with React.FC<> with generics as return type
    - Store the arrow function in const reference
    - Don't use Logic as suffix for const reference name
    - create code block and destructure the props object in first line of the arrrow function
    - export default statements on end of the file

    Example 1

    ```Typescript
        import React from "react";
        import HomeView from "./Home.view";

        interface IHomeProps {
            title: string
        }

        const Home: React.FC<IHomeProps> = (props: IHomeProps) =>  {
            const {title}: IHomeProps = props
            // write logics like useState, useEffect, methods

            // If you want to access the state or methods then pass that as props to View file
            return <HomeView title={title} />
        }

        export default Home;
    ```

    Example 2

    ```Typescript
        import React from "react";
        import HomeView from "./Home.view";

        interface IHomeProps {
            title: string
            subTitle: string
            paragraph: string
        }

        const Home: React.FC<IHomeProps> = (props: IHomeProps) => {
            const {title, subTitle, paragraph} = props
            // write logics like useState, useEffect, methods

            // If you want to access the state or methods then pass that as props to View file
            return (
                <HomeView 
                    title={title} 
                    subTitle={subTitle}
                    paragraph={paragraph}
                />
            )
        }
        
        export default Home;
    ```

#### Functions

1. Please avoid creating functions inside the html.  For example,

```js
<div className={clearButtonStyle} onClick={()=>{ setValue("");}}>
  <img src={clearButton} alt="clear button loading" />
</div>
```

Basically, this will create a new function every time while re-rendering the component. So pls avoid doing this. Instead you can create a function and directly refer it. Like the below one.

```js
const setEmptyValue = ()=>{ setValue("");}

return (
      <div className={clearButtonStyle} onClick={setEmptyValue}>
        <img src={clearButton} alt="clear button loading" />
      </div>
  );
```

## React Testing

### Naming Convention

1. File name

    - Extensions: Use spec.tsx extension for React Test Files

1. data-testid

    - Use `tid` as the prefix to all data-testid in JSX Element to avoid conflicts.  
    - For example, `tid-home`, `tid-contact`

### Three Layered Unit Tests

- Layer 1: Unit that you want to test, or test requirement
- Layer 2: Specific action or scenario you want to test
- Layer 3: Describe the expected result

#### Template

```Typescript
    // Layer 1
    describe("Unit or Component Under Test", () => {

        // Layer 2
        describe("Scenerio", () => {

            //Layer 3
            test("Expected Behaviour", () => {

            })

            // Layer 3
            test("Expected Behavior", () => {

            })
        })

        // Layer 2
        describe("Scenerio", () => {

            // Layer 3
            test("Expected Behaviour", () => {

            })

            // Layer 3
            test("Expected Behavior", () => {

            })
        })
    })
```

#### Example

```Typescript
    describe('Order Component Tests', () => {

        describe('Add a new item', () => {

            test('When item is already in shopping basket, expect item count to increase', () => {
                // ...
            })

            test('When item does not exist in shopping basket, expect item count to equal one', () => {
                // ...
            })
        })
    })
```

### beforeEach and afterEach with mock data

#### template

```Typescript

    // write all mock data here

    describe("Unit or Component Under Test", () => {

        beforeEach(() => {

        })

        afterEach(() => {

        })

        describe("Scenerio", () => {

            test("Expected Behaviour", () => {

            })

            test("Expected Behavior", () => {

            })
        })

        describe("Scenerio", () => {

            test("Expected Behaviour", () => {

            })

            test("Expected Behavior", () => {

            })
        })
    })
```

Example

```Typescript
    import { screen } from "@testing-library/react"
    import createMockStore, { MockStoreCreator, MockStoreEnhanced } from "redux-mock-store";
    import renderReducer from "../../../shared/utils/test-utils";
    import LearnerProfile from "../Index"

    type MockState = {
        searchInput: {
            value: string;
            error: boolean;
        };
    }

    const mockState: MockState = {
        searchInput: {
            value: "",
            error: false
        }
    };

    const mockStore: MockStoreCreator<unknown, {}> = createMockStore([]);

    const store: MockStoreEnhanced<unknown, {}> = mockStore(mockState);

    describe("Profile Component Tests", () => {

        beforeEach(() => {
            renderReducer(<LearnerProfile />, { store });
        })

        describe("Rendering the Profile Component", () => {

            test("Should Render the Profile", () => {
                const learnerProfileElement: HTMLElement = screen.getByTestId("tid-learner-profile")

                expect(learnerProfileElement).toBeInTheDocument();
            })
        })
    })
```

### Install eslint for testing

- __eslint-plugin-testing-library__
- It codifies a whole bunch of best practices

#### Example Rules

- __prefer-user-event ESLint rule__
- __prefer-screen-queries ESLint rule__

### Events Testing

- __fireEvent vs userEvent__
  - The core premise of React Testing Library is testing React components how users interact with them instead of how the code is implemented.
  - The primary way that users interact with our components is through actions (clicking, typing, hovering, etc)
  - fireEvent was considered too low-level and the user-event library was introduced to simulate user interactions

- __fireEvent__
  - __prefer-user-event ESLint rule__ enforces the usage of userEvent over fireEvent
  - Need to specify e.target.value. Definitely to low-level. Instead, should use the type user event

```Typescript
    import React from "react"
    import { fireEvent, render, screen } from "@testing-library/react"

    test("types into text box", () => {
        render(<textarea />)

        const textBox = screen.getByRole("textbox")
        // ⚠️ `prefer-user-event` ESLint error
        // don't use `fireEvent`
        fireEvent.change(textBox, {
            target: {
                value: "Hello,\nWorld!",
            },
        })

        expect(textBox).toHaveValue("Hello,\nWorld!")
    })
```

- __userEvent__
  - The type user event writes the specified text into the `<textarea>`, character by character
  - This actually triggers onChange events for each character typed, just like what would happen when a real user types into a text box
  - We even have to specify {enter} (hitting the ENTER key) instead of a line break (\n)
  - The text box is also “clicked” before typing

```Typescript
    import React from "react"
    import { render, screen } from "@testing-library/react"
    import userEvent from "@testing-library/user-event"

    test("types into text box", () => {
        render(<textarea />)

        const textBox = screen.getByRole("textbox")
        // 👍🏾 `type` writes text inside of the `<textarea>`
        // character-by-character triggering multiple `onChange` events
        userEvent.type(textBox, "Hello,{enter}World!")

        expect(textBox).toHaveValue("Hello,\nWorld!")
    })
```

### Proper use of queries or get

```Typescript
    import React from "react"
    import { render } from "@testing-library/react"
    import Greeting from "./Greeting"

    test("renders a message", () => {
        const { getByText } = render(<Greeting />)

        // ⚠️ `prefer-screen-queries` ESLint error
        // don't destructure, `render`, use `screen` instead
        const helloWorldText = getByText("Hello, world!")
        
        expect(helloWorldText).toBeInTheDocument()
    })
```

- DOM Testing Library, which React Testing Library is built on top of, now exposes a screen object which has every query built-in
- The changed best practice is to always use screen object and no longer destructure the object returned by render
- __prefer-screen-queries ESLint rule__ ensures to follow this best practice

```Typescript
    import { render, screen } from "@testing-library/react"
    import Greeting from "./Greeting"

    test("renders a message", () => {
        render(<Greeting />)

        const helloWorldText = screen.getByText("Hello, world!")

        // 👍🏾 use `screen` object queries instead
        expect(helloWorldText).toBeInTheDocument()
    })
```

## SCSS

1. Use `elr` as the prefix to all class names to avoid conflicts.  For example, `elr-home`, `elr-contact`
2. Follow [BEM](http://getbem.com/) methodology while defining the class names. For example, `elr-button`, `elr-button--primary`, `elr-button--secondary`, `elr-list`, `elr-list__item` and so on.,
