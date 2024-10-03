# Context Practice

In this exercise, you will practice using React contexts while gaining
familiarity with the Vitest testing framework for React. By the end, you should
be able to:

* Connect a React component to a context
* Change the content of a React component dynamically based on context
* Change the context from a React component
* Create a custom React context-wrapper hook
* Run React Testing Library / Vitest tests and use any error messages to help
  debug your code

## Resources

You can use any of the following resources during this practice:

* [React documentation]
* [Mozilla Developer Network]
* [React Testing Library documentation][React Testing Library]
* [Vitest documentation][Vitest]
* Any of your previous projects or assessments

## Tests

To help you complete the phases below, this practice contains tests written
using [React Testing Library] (RTL) on a [Vitest] framework. (Vitest is based on
the [Jest] framework but is built to take advantage of Vite's module-based
approach.)

As a testing suite, RTL focuses on the code's behavior / the user experience. It
accordingly enables you to easily test anything that a user might see--e.g.,
whether or not a component's text updates appropriately--or do, such as clicking
a button.

In general, RTL is not a good tool for interrogating the underlying structure
and mechanics that produce your app's behavior. For example, it does not allow
you to grab an HTML element by its class name. (After all, a user will never
know a `div`'s class name, or even that a given portion of the page is a `div`!)

This inability to test implementation details easily may seem frustrating, but
truthfully it is quite helpful: focusing your tests on behavior rather than
implementation frees you to refactor and improve your code without having to
rewrite all your tests. Want to make a `div`'s class name more semantic? No
problem! What if you decide to use Redux instead of Context, or convert an app's
class components to function components? Once again, no big deal. The tests
don't care how you get your app to produce the desired behavior as long as it
does, indeed, produce the desired behavior.

> **Note:** If necessary, your tests can still grab an HTML element by its class
> name using, e.g., vanilla JavaScript. What RTL encourages you to think about,
> however, is whether or not that is actually a helpful test to run.

The tests for this practice are grouped by phase. Before starting a phase, run
the tests; they should all fail. You will have finished implementing the
functionality for that phase once all the tests turn green.

The tests are located in __src/\_\_tests\_\___. Look through the test files and
try to understand what they are doing. You should not modify the files in that
directory, however.

> **Note:** These tests determine whether or not your code meets the
> **functionality** expectations. It is still up to you to make sure that your
> code is well formatted and does not produce any errors in the console.

## Recommendations and requirements

Review your app's output in the terminal or browser console frequently to make
sure that you do not have any warnings about things like unused variables.

After each phase, the application should render in the browser without errors.

Do not move any files in the __src/components__ folder. The tests expect those
files to be where they are.

When the instructions say to do something like "Use the `XXX` component in the
`render` method", recognize that you may need to import something (like the
`XXX` component) before that will work. In most cases, you will **NOT** be
instructed to import anything. Use your knowledge of JavaScript modules to
figure that out on your own.

## Phase 0: Getting the app running

This starter contains an application generated by Vite using
`appacademy/react18-vite-vitest-template`.

It also contains the tests for the components that you will create.

The React application is already wrapped in the `CoffeeProvider` (from
__src/context/CoffeeContext.jsx__) component in __src/main.jsx__.

After cloning, run `npm install` to install the dependencies.

You can run your tests with `npm test`. Follow the on-screen instructions to
quit the test runner. If you want to run your tests only once, use the following
command:

```plaintext
CI=true npm test
```

To run the tests for your current step, run `npm test <file>`, where `<file>`
is the test file you're working on.

Here's the list of test files to run individually:

* `npm test 1-SelectedCoffeeBean`
* `npm test 2-SetCoffeeBean`

Type `Ctrl+c` to stop the test runner.

You can also run all the tests at once simply by running `npm test`.

To run the application in a browser, use the command `npm run dev` and then
navigate to [http://localhost:5173] in your browser.

## Phase 1: SelectedCoffeeBean

In this phase, you will be filling in the code for the `SelectedCoffeeBean`
component which will show the name of the selected coffee bean extracted from
a context.

Take a look at the context and provider created in
__src/context/CoffeeContext.jsx__. The value of the `CoffeeContext` has a
`coffeeBean` that should be used in the `SelectedCoffeeBean` component.

To test this phase, run `npm test 1-SelectedCoffeeBean`.

Start by rendering the `SelectedCoffeeBean` component inside of `App` so you can
test changes to `SelectedCoffeeBean` in a browser. Inside `SelectedCoffeeBean`,
print the name of the selected coffee bean inside the `h2` element.

**Note:** Do not create a custom hook to return the values of the
`CoffeeContext` at this point. You will do that below once you have everything
working.

## Phase 2: SetCoffeeBean

In the previous phase, you used the `CoffeeContext`'s `coffeeBean` value. In
this phase you will set the `coffeeBean` value of the context in the
`SetCoffeeBean` component.

To test this phase, run `npm test 2-SetCoffeeBean`.

Begin by rendering the `SetCoffeeBean` component inside of the `App` component.
An array of coffee beans has already been imported from the
__src/mockData/coffeeBeans.json__ mock data file; pass the array to the
`SetCoffeeBean` component as a `coffeeBeans` prop.

A `select` element with `option`s has been rendered for you in the
`SetCoffeeBean` component. Make the `select` a _controlled input_ that changes
the value of the `coffeeBean` in the `CoffeeContext` using the `setCoffeeBeanId`
function from the `CoffeeContext`. Finally, initialize the `select`'s `value`
attribute to the `id` of the initially selected coffee bean.

If done correctly, you should see the name of the coffee bean in the
`SelectedCoffeeBean` component change whenever you select a new option. The
third and final test in this suite checks to make sure that this works /
everything is properly integrated.

## Phase 3: Refactor!

Now that your code is working and covered by tests, it's time to refactor!

First, make sure that you have committed your working code so it is easy to
restore a functioning version should your refactor go awry. Then create a custom
`useCoffee` hook to return the values of the `CoffeeContext`. You should define
this hook in __src/context/CoffeeContext.jsx__; you will call it in the
`SelectedCoffeeBean` component.

This change shouldn't modify the behavior of your app, so your tests should
still run green. Run `npm test` to go through every test. As long as they all
stay green, you can have confidence that you've implemented the change
correctly!

## What you have learned

In this practice, you've learned how to send and receive updates from/to your
React components using context. You also created a custom hook and gained
valuable experience using RTL/Vitest tests to check your work and help debug.

[React documentation]: https://react.dev/
[Mozilla Developer Network]: https://developer.mozilla.org/en-US/docs/Web
[React Testing Library]: https://testing-library.com/docs/react-testing-library/intro/
[Vitest]: https://vitest.dev/
[Jest]: https://jestjs.io/docs/getting-started
[http://localhost:5173]: http://localhost:5173
# context-practice-2
