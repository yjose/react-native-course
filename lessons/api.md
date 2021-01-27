---
path: "/network-api"
title: "Network API"
order: "4E"
section: "Advanced"
description: "Learn React Native With Youssouf El Azizi"
---

React Native provides the Fetch API for your networking needs. Fetch will seem familiar if you have used XMLHttpRequest or other networking APIs before. You may refer to [MDN's guide on Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) for additional information.

That means all solutions you already have the chance to use in your reactjs App will work the same in mobile.

## React-query

React Query is often described as the missing data-fetching library for React, but in more technical terms, it makes fetching, caching, synchronizing and updating server state in your React applications a breeze.

Those some features we will benefits from by default using `react-query` :

- Queries, Mutations, Parallel Queries,Dependent Queries,Paginated Queries,Infinite Queries
- Caching, Cache Manipulation,Offline Caching, Optimistic Ui
- Prefetching APIs, Query Cancellation, React Suspense (Experimental)

### Installation & Usage

Install `react-query`

```bash
yarn add react-query
```

This example very briefly illustrates How to use React Query:

```jsx
import * as React from "react";
import { QueryClient, QueryClientProvider, useQuery } from "react-query";
import { View, Text } from "ui";
// Create a client
const queryClient = new QueryClient();

export default function App() {
  return (
    // Provide the client to your App
    <QueryClientProvider client={queryClient}>
      <Example />
    </QueryClientProvider>
  );
}

function Example() {
  // Queries
  const { isLoading, error, data } = useQuery("repoData", () =>
    fetch("https://api.github.com/repos/yjose/reactjs-popup").then((res) =>
      res.json()
    )
  );

  if (isLoading) return <Text> Loading... </Text>;

  if (error) return <Text> An error has occurred: + {error.message}</Text>;

  return (
    <View flex={1} justifyContent="center" alignItems="center">
      <Text>{data.name}</Text>
      <Text>{data.description}</Text>
      <Text>👀 {data.subscribers_count}</Text>
      <Text>✨ {data.stargazers_count}</Text>
      <Text>🍴 {data.forks_count}</Text>
    </View>
  );
}
```

### Setup react-query

Create a new folder `src/api` to create a global provider and our client instance:

```tsx
//src/client.tsx
import axios from "axios";

const BASE_URL = "";

export const client = axios.create({
  baseURL: BASE_URL,
});
```

Create a APIProvider and Make to add it to your root tree `App.tsx`

```tsx
//src/APIProvider.tsx
import React from "react";
import { QueryClient, QueryClientProvider } from "react-query";

// Create a client
const queryClient = new QueryClient();

type Props = {
  children: React.ReactNode;
};

export const APIProvider = ({ children }: Props) => {
  return (
    <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>
  );
};
```

Now you are ready to start creating Quires and Mutation:

```tsx
// Query
//api/useTasks.tsx

import { useQuery } from "react-query";
import { client } from "./client";

type TaskType = {
  label: string;
  done: boolean;
  color: string;
};

const getTasks = async () => {
  const { data } = await client.get("/task");
  return data;
};

export function useMe() {
  return useQuery<TaskType[]>("tasks", getTasks);
}
```

```jsx
// Mutation
//api/useAddTask.tsx
import { useMutation } from "react-query";
import { client } from "./client";

type TaskType = {
  label: string,
  done: boolean,
  color: string,
};

export function useAddTask() {
  return useMutation((data: TaskType) => client.post("/task", data));
}
```

## 🧑‍💻 Exercise

Update `Home` Screen to use Data from API

- Base Url : `https://60020b0d08587400174db917.mockapi.io/api/`
- Get All tasks : GET --> `/task`
- Get Task by Id : GET --> `/task/:id`
- Create New Task : POST --> `/task`
- Update task : PUT --> `/task/:id`
- Delete Task : DELETE --> `/task/:id`

### Helpful Links

- [React Query](https://react-query.tanstack.com/)
