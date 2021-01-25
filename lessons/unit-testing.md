---
path: "/unit-testing"
title: "Unit testing"
order: "4C"
section: "Advanced"
description: "Learn React Native With Youssouf El Azizi"
---

React Native Testing Library is a testing library for React Native inspired by React Testing Library. Because React Native does not run in a browser environment, the core queries are implemented independently, unlike other wrappers that use DOM Testing Library as the base.

It provides light utility functions on top of `react-test-renderer`, in a way that encourages better testing practices.

## Install library

```bash
yarn add --dev @testing-library/react-native  @testing-library/jest-native
```

## Configuration

Create `jest.config.json` file configuration :

```json
{
  "preset": "react-native",
  "setupFilesAfterEnv": ["@testing-library/jest-native/extend-expect"]
}
```

## Write Tests

Create a file inside `__tests__`folder and start testing your components
A simple unit test for a `Counter` Components.

```tsx
import "react-native";
import React from "react";
import { fireEvent, render } from "@testing-library/react-native";

it("renders correctly", () => {
  // render component
  const { getByText } = render(<Counter />);

  // get buttons and text elements
  const decrement = getByText(/decrement/i);
  const increment = getByText(/increment/i);
  const counterText = getByText(/Current count:/i);

  // Make sure you have the right values
  expect(counterText.props.children).toEqual(["Current count: ", 0]);
  // trigger an event
  fireEvent.press(increment);
  expect(counterText.props.children).toEqual(["Current count: ", 1]);
  fireEvent.press(decrement);
  expect(counterText.props.children).toEqual(["Current count: ", 0]);
});
```

## More Examples

- 👆 [Clicking buttons and asserting onPress' outcome](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/Counter.test.tsx).
- 📲 [Filling a simple login form and asserting successful submission](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/LoginSubmission.test.tsx).
- 🎣 [Custom hook testing (number of alternatives)](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/CounterUsesCustomHook.test.tsx).
- 📡 [Mocking fetch calls](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/LoginSubmission.test.tsx#L36).
- 🧭 [Mocking navigation through screens](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/LoginSubmission.test.tsx#L13). ([react navigation v5](https://reactnavigation.org/))
- 🔚 [E2E feel due to real navigation throughout screens](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/Home.test.tsx).
- 📥 [Handling and mocking providers](https://github.com/vanGalilea/react-native-testing/blob/master/src/test/test-utils.tsx).
- 📹 [Mocking external lib.'s components](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/Video.test.tsx).
- 🎭 [Mocking and interacting with RN's Modal component](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/Modal.test.tsx).
- 🧾 [Handling with a screen with RN's FlatList component](https://github.com/vanGalilea/react-native-testing/blob/master/__tests__/FlatList.test.tsx).

## 🧑‍💻 Exercise

Test our Login Form to Make sure it :

- renders correctly
- should display required error when values are empty
- should display matching error when email is invalid
- should call login whit correct values when values are valid

### Helpful Links

- [React Native Testing Library](https://github.com/callstack/react-native-testing-library)
- [Custom jest matchers to test the state of React Native](https://github.com/testing-library/jest-native)
