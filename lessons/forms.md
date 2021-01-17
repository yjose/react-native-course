---
path: "/forms"
title: "Forms"
order: "4B"
section: "Advanced"
description: "Learn React Native With Youssouf El Azizi"
---

Handling forms in react native is a crucial task in your journey as a react native developer, you can’t think about developing a new react native app without dealing with forms, at least for login and sign up screen in case your app is retrieving data in the most of the cases. Finding a solution for such a repetitive task will help you save a lot of time .

Through My 3 years experience As a react native developer, I used to use different approaches.
Recently I end up using `react-hook-form` to manage Forms for react native.

### Why React-hooks-form

Form [React-hook-form official documentation](https://react-hook-form.com/), one of the primary goals of React Hook Form is to reduce the amount of code that you have to write. React hooks form is really easy to use and it takes a small amount of code. More than that if we can compare `react-hook-form` to the most used solution to handle forms in React such as `Formik` and `redux-form`, it seems clear that [`react-hook-form` will be the winner regarding bundle size and performance.](https://react-hook-form.com/#codeComparison)

### Install React-hooks-form

Install react-hook-library

```bash
yarn add react-hook-form
```

Example
TODO :

- register link
- create a custom
- Validation
- create an input with the following props

```ts
interface Props extends TextInputProps {
  name: string;
  disabled?: boolean;
  label?: string;
  error?: FieldError | undefined;
}
```

Create Input Component

```jsx
```

Validation

```jsx
```

Create Form

```tsx
import React from "react";
import { Text, View, TextInput, Button, Alert } from "react-native";
// form types
type FormData = {
  firstName: string;
  lastName: string;
};

import { useForm, Controller } from "react-hook-form";

export default function App() {
  const { control, handleSubmit, errors } =
    useForm < FormData > { defaultValues: {} };
  const onSubmit = (data) => console.log(data);

  return (
    <View>
      <Controller
        control={control}
        render={({ onChange, onBlur, value }) => (
          <TextInput
            style={styles.input}
            onBlur={onBlur}
            onChangeText={(value) => onChange(value)}
            value={value}
          />
        )}
        name="firstName"
        rules={{ required: true }}
        defaultValue=""
      />
      {errors.firstName && <Text>This is required.</Text>}

      <Controller
        control={control}
        render={({ onChange, onBlur, value }) => (
          <TextInput
            style={styles.input}
            onBlur={onBlur}
            onChangeText={(value) => onChange(value)}
            value={value}
          />
        )}
        name="lastName"
        defaultValue=""
      />

      <Button title="Submit" onPress={handleSubmit(onSubmit)} />
    </View>
  );
}
```

## Example

## 🧑‍💻 Exercise

Implement `react-hook-form` with Validation for the login form screen.

### Helpful Links

- [React Hook form](https://react-hook-form.com/)
- [Forms in React Native, The right way](https://elazizi.com/forms-in-react-native-the-right-way)
