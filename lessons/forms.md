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

Refactor your custom input to support the following `Props` interface.

```ts
interface Props extends TextInputProps {
  name: string;
  disabled?: boolean;
  label?: string;
  error?: FieldError | undefined;
}
```

Typing and Validation

```jsx
type FormData = {
  email: string,
  password: string,
};

const validation = {
  email: {
    required: { value: true, message: "Email is required" },
    pattern: {
      value: /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/,
      message: "Invalid Email Format",
    },
  },
  password: {
    required: { value: true, message: "Password is required" },
  },
};
```

Create Form

```tsx
export const Login = () => {
  const { handleSubmit, errors, setValue, register } = useForm<FormData>();

  const onSubmit = (data: FormData) => {
    console.log(data);
  };
  React.useEffect(() => {
    register("email", validation.email);
    register("password", validation.password);
  }, [register]);
  return (
    <View flex={1} justifyContent="center" padding="m">
      <Text variant="header" textAlign="center">
        Sign in
      </Text>
      <View marginVertical="xl">
        <Input
          placeholder="Email"
          onChangeText={(t) => setValue("email", t)}
          error={errors["email"]}
        />
        <Input
          placeholder="Password"
          onChangeText={(t) => setValue("password", t)}
          error={errors["password"]}
        />
        <Text color="grey" textAlign="right">
          FORGOT?
        </Text>
      </View>
      <Button label="Sign in" onPress={handleSubmit(onSubmit)} />
      <Button variant="outline" label="Create account" onPress={() => {}} />
    </View>
  );
};
```

## 🧑‍💻 Exercise

Use `react-hook-form` to implement login form with Validation.

### Helpful Links

- [React Hook form](https://react-hook-form.com/)
- [Forms in React Native, The right way](https://elazizi.com/forms-in-react-native-the-right-way)
