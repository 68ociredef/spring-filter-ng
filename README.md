# Spring-filter-ng

A filter builder to manage [Spring Filter](https://github.com/turkraft/spring-filter) library for Angular application.

<a href="https://www.npmjs.com/~68ociredef" target="_blank"><img src="https://img.shields.io/npm/v/spring-filter-ng" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~68ociredef" target="_blank"><img src="https://img.shields.io/npm/dm/spring-filter-ng" alt="NPM Downloads" /></a>
<a href="https://www.npmjs.com/~68ociredef" target="_blank"><img src="https://img.shields.io/npm/dt/spring-filter-ng" alt="NPM Downloads total"/></a>

## Getting started

Install Spring filter ng

```
npm install spring-filter-ng
```

## Angular Support

 Angular   | Spring-filter-ng | Status      |
 ----------| ---------------  | ----------- |
 14        | 3.x              | Active      |
 12/13     | 1.x+             | -           |


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
  this.fetchApiService.getStuffsByFilter(options)......
  

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
  manager: Employee;
  staff: Employee[];
}

 
1. If you want to know the employees who receive a salary greater than 3000:

 const filter = SpringFilter.new().greaterThen("employee.salary", 3000).value;
 
2. If you want to know the employees who have marital status divorced or separated and have 
   at least two stuff members or are not manager:

 const filter = SpringFilter.new().append("maritalStatus").in("divorced", "separated")
    .and(SpringFilter.new().greaterThan(springFilter.instance().size("staff"), 2).or("manager").isNotNull()).value;
    

```
## Utils

It is possbile to use utils method from <strong>SpringFilterUtils </strong>.

<table>
  <thead>
    <tr>
     <th> <strong> Name </strong> </th>
     <th> <strong> Description </strong> </th>
    </tr>
  </thead>
  <tbody>
    <tr>
     <td> likeAll(parameter) </td>
     <td> Search for values that have the parameter in input in any position </td>
    </tr>
    <tr>
     <td> likeLeft(parameter) </td>
     <td> Search any values that start with the parameter in input.</td>
    </tr>
    <tr>
     <td> likeRight(parameter) </td>
     <td> Search any values that end with the parameter in input.</td>
    </tr>
    <tr>
     <td> addAND(filter, parameter) </td>
     <td> Conditional append and condition </td>
    </tr>
    <tr>
     <td> addOR(filter, parameter) </td>
     <td> Conditional append or condition </td>
    </tr>
    <tr>
     <td> addNOT(filter, parameter) </td>
     <td> Conditional append not condition </td>
    </tr>
    <tr>
     <td> isANumber(value) </td>
     <td> Check the value in input is a number </td>
    </tr>
    <tr>
     <td> isAString(value) </td>
     <td> Check the value in input is a string </td>
    </tr>
    <tr>
     <td> isADate(value) </td>
     <td> Check the value in input is a date </td>
    </tr>
  </tbody>
  
</table>

## Compact expressions.

It is possible to use expressions more compact in this way:

```ts

const filter = new SpringFilter()
    .build() 
    .orLike("firstName", SpringFilterUtils.likeRight(value))
    .orLike("lastName", SpringFilterUtils.likeRight(value))
    .andEquals("id", value).value
 

```

## Date builder

It is possible to use a date builder to manage date input.

### Configuration's parameter

 Param     | default value   | 
 ----------| --------------- | 
 localeFe  | en              | 
 localeBe  | en              | 
 literalFe | /               |
 literalBe | /               |

### Example

Format the date in local date time adding a day, in italian format.

```ts
import {SfDateBuilder } from 'spring-filter-ng';
```
```ts

 const data = new SfDateBuilder()
     .configure({localeFe:'it'})
     .build()
     .localDateTime(value) 
     .dayAfter()
     .value()

```


Love **spring-filter-ng** ? Give to repo a **star** :star:.



