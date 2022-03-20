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

Considering an employee

interface Employee {
  id: number;
  firstName: string;
  lastName: string;
  birthDate: string;
  maritalStatus: string;
  salary: number;
  manager: Employee
  staff: Employee[]
}

1. If you want to know the employees who receive a salary greater than 3000:

 const filter = filterBuild.greaterThen("employee.salary",3000).value;
 
2. If you want to know the employees who have marital status divorced or separated and have 
   at leat two stuff members or are not manager:

 const filter = filterBuild.append("maritalStatus").in("divorced", "separated")
    .and(base.instance().greaterThan(base.instance().size("staff"),2).or("manager").isNotNull()).value

```



