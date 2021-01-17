---
path: "/unit-testing"
title: "Unit testing"
order: "4C"
section: "Advanced"
description: "Learn React Native With Youssouf El Azizi"
---

React Native Testing Library is a testing library for React Native inspired by React Testing Library. Because React Native does not run in a browser environment, the core queries are implemented independently, unlike other wrappers that use DOM Testing Library as the base.

It provides light utility functions on top of react-test-renderer, in a way that encourages better testing practices.

## Install library

```bash
yarn add --dev @testing-library/react-native  @testing-library/jest-native
```

## Configuration

Create `jest.config.js` file configuration :

```json
{
  "preset": "react-native",
  "setupFilesAfterEnv": ["@testing-library/jest-native/extend-expect"]
}
```

## Example

## 🧑‍💻 Exercise

### Helpful Links

- [React Native Testing Library](https://github.com/callstack/react-native-testing-library)
