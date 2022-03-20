# Spring-filter-ng

A filter builder to manage [Spring Filter](https://github.com/turkraft/spring-filter) library for Angular application.

## Getting started

Install Spring filter ng

```
npm install spring-filter-ng
```

## Usage

```ts
import {SpringFilter, SpringFilterUtils } from 'spring-filter-ng';
```

```ts
...

public searchByFilter() {
  const filter = new SpringFilter().build(); //initialize filter
  
  filter.equals("email","example@mail.it").value;
  
  const options = SpringFilterUtils.setOptions(value);
  
  this.fetchApiService.getClienteByFilter(options)......
  

}
```
