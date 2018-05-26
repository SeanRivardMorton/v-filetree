# A base Vuetify + Typescript file tree viewer.

> Simple component to use until Vuetify implements their own file tree viewer. 

> This small block is using typescript and `vue-class-decorators`.
> If I need to implement this component in a different project, I will 

# Example usage:

> place this in `<template>`

```<masv-file-tree :model="treeData"></masv-file-tree>```

> Place this in `<script lang="ts"`

```
export default class extends Vue {

treeData = {
    name: 'My Tree',
    children: [
      { name: 'hello' },
      { name: 'wat' },
      {
        name: 'child folder',
        children: [
          {
            name: 'child folder',
            children: [{ name: 'hello' }, { name: 'wat' }]
          },
          { name: 'hello' },
          { name: 'wat' },
          {
            name: 'child folder',
            children: [{ name: 'hello' }, { name: 'wat' }]
          }
        ]
      }
    ]
  };
  ```
