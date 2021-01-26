---
path: "/network-api"
title: "Network API"
order: "4E"
section: "Advanced"
description: "Learn React Native With Youssouf El Azizi"
---

React Native provides the Fetch API for your networking needs. Fetch will seem familiar if you have used XMLHttpRequest or other networking APIs before. You may refer to[ MDN's guide on Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) for additional information.

That means all solutions you already have the chance to use in your reactjs App will work the same in mobile.

## React-query

React Query is often described as the missing data-fetching library for React, but in more technical terms, it makes fetching, caching, synchronizing and updating server state in your React applications a breeze.

Install `react-query`

```bash
yarn add react-query
```

```jsx
import { QueryClient, QueryClientProvider, useQuery } from "react-query";

const queryClient = new QueryClient();

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Example />
    </QueryClientProvider>
  );
}

function Example() {
  const { isLoading, error, data } = useQuery("repoData", () =>
    fetch("https://api.github.com/repos/yjose/reactjs-popup").then((res) =>
      res.json()
    )
  );

  if (isLoading) return <Text> Loading... </Text>;

  if (error) return <Text> An error has occurred: + {error.message}</Text>;

  return (
    <View>
      <Text>{data.name}</Text>
      <Text>{data.description}</Text>
      <Text>👀 {data.subscribers_count}</Text>
      <Text>✨ {data.stargazers_count}</Text>
      <Text>🍴 {data.forks_count}</Text>
    </View>
  );
}
```

## Example

## 🧑‍💻 Exercise

### Helpful Links

- [React Native Testing Library](https://github.com/callstack/react-native-testing-library)
