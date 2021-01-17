---
path: "/lists"
title: "Lists"
order: "3D"
section: "Basic"
description: "Learn React Native With Youssouf El Azizi"
---

React Native provides a suite of components for presenting lists of data. Generally, you'll want to use either FlatList or SectionList.

## FlatList

The `FlatList` component requires two props: `data` and `renderItem`.

- `data` is the source of information for the list.
- `renderItem` takes one item from the source and returns a formatted component to render.

```jsx
import React from "react";
import { FlatList, StyleSheet, Text, View } from "react-native";

const FlatListBasics = () => {
  return (
    <View style={styles.container}>
      <FlatList
        data={[
          { key: "Devin" },
          { key: "Dan" },
          { key: "Dominic" },
          { key: "Jackson" },
          { key: "James" },
          { key: "Joel" },
          { key: "John" },
          { key: "Jillian" },
          { key: "Jimmy" },
          { key: "Julie" },
        ]}
        renderItem={({ item }) => <Text style={styles.item}>{item.key}</Text>}
      />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    paddingTop: 22,
  },
  item: {
    padding: 10,
    fontSize: 18,
    height: 44,
  },
});
```

## SectionList

SectionList is a similar to FlatList, but it allows you to render items in sections with a header item between. The `data` for the `SectionList` is still an array, but each array item will need to be an object with a title (a string) and a data (an array) prop.

Additionally you can pass in a prop called `renderSectionHeader` which will let you render the title for each section.

```jsx
import React from "react";
import { SectionList, StyleSheet, Text, View } from "react-native";

export const SectionListExample = () => {
  return (
    <View style={styles.container}>
      <SectionList
        sections={[
          { title: "D", data: ["Devin", "Dan", "Dominic"] },
          {
            title: "J",
            data: [
              "Jackson",
              "James",
              "Jillian",
              "Jimmy",
              "Joel",
              "John",
              "Julie",
            ],
          },
        ]}
        renderItem={({ item }) => <Text style={styles.item}>{item}</Text>}
        renderSectionHeader={({ section }) => (
          <Text style={styles.sectionHeader}>{section.title}</Text>
        )}
        keyExtractor={(item, index) => index}
      />
    </View>
  );
};
```

### React Native Lists Features

flat lists, supporting the most handy features:

- Fully cross-platform.
- Optional horizontal mode.
- Configurable viewability callbacks.
- Header support.
- Footer support.
- Separator support.
- Pull to Refresh.
- Scroll loading.
- ScrollToIndex support.
- Multiple column support.

### List props

The list elements have a bunch of built in properties to help customize for your experience. Check out the [FlatList](https://reactnative.dev/docs/flatlist) and [SectionList](https://reactnative.dev/docs/sectionlist) docs for all of them. Here are some I tend to use most often:

- `ItemSeparatorComponent`- renders a custom separator between your items. Handy if you have to e.g. render a line or even something dynamic instead of building it into the list items
- `ListEmptyComponent` - this is rendered when the data is an empty array or undefined. Saves you from doing conditional rendering manually!
- `ListFooterComponent` - renders something at the bottom of the list
- `ListHeaderComponent` - renders something at the top of the list
- `extraData` - the list only gets re-rendered if the DATA changes. It might happen though that what you display depends on some external factors. In this case use the extraData to pass in any variables that should also trigger a re-render when changed
- `horizontal` - render the list horizontally instead of vertically
- `numColumns` - render multiple columns
  onEndReached - fires when the user has scrolled to the end of the list. Handy for pagination

## 🧑‍💻 Exercise

Implement the `Home` Screen using FlatList Component.

=> Screen Here

> Create a new folder for `Home` screen under `screens`.

### Helpful Links

- [React Native Testing Library](https://github.com/callstack/react-native-testing-library)
