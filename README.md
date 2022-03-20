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

  //initialize filter
  const filterBuild = new SpringFilter().build(); 
  
  //Build query
  const filter = filterBuild.equals("email","example@mail.it").value;
  
  //Set parametrs for angular http.
  const options = SpringFilterUtils.setOptions(value);
  
  //Fetch datas.
  this.fetchApiService.getClienteByFilter(options)......
  

}
```

## Example

```ts



```

