# SearchService

All URIs are relative to *https://search-engine-walkover.el.r.appspot.com*

Method | HTTP request | Description
------------- | ------------- | -------------
[**addIndex**](SearchService.md#addIndex) | **POST** /addIndexByApi | Add Index By Api
[**addObject**](SearchService.md#addObject) | **POST** /add/{index_name} | This will add an object to the given index.
[**addObjects**](SearchService.md#addObjects) | **POST** /bulkadd/{index_name} | This will add an array of objects to the given index.
[**copyIndexConfig**](SearchService.md#copyIndexConfig) | **POST** /copyIndexConfig | Copy Index configuration from one index to another
[**deleteIndex**](SearchService.md#deleteIndex) | **DELETE** /deleteIndexByApi | Delete Index
[**deleteObject**](SearchService.md#deleteObject) | **DELETE** /delete/{index_name} | This will delete the object with given object id
[**generateEvent**](SearchService.md#generateEvent) | **POST** /event/{index_name} | This will generate an event.
[**getAllObjects**](SearchService.md#getAllObjects) | **POST** /getAllObjects | Get All objects stored in index
[**getAllIndices**](SearchService.md#getAllIndices) | **POST** /getAllIndices | Get all indices
[**searchQuery**](SearchService.md#searchQuery) | **POST** /search/{index_name} | 

<a name="mandatoryStep">

# **Mandatory Step**
NOte: perform this step before any of the given methods

first add these statements to your app.module.ts file, This is the first step to use any of the given function
```typescript
import { ApiModule } from 'universal-search-engine-angular';
import { HttpClientModule } from '@angular/common/http';


@NgModule({
    imports: [
        ApiModule,
        // make sure to import the HttpClientModule in the AppModule only,
        // see https://github.com/angular/angular/issues/20575
        HttpClientModule
    ],
    declarations: [ AppComponent ],
    providers: [],
    bootstrap: [ AppComponent ]
})
export class AppModule {}
```


<a name="addIndex"></a>
# **addIndex**
> Object addIndex(name, type, API_KEY)

first perform this [**step**](#mandatoryStep)

Add Index By Api

Add Index by Api, provide name and type for creating new index

### Example


```typescript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {
    
    var name = "name_example"; // String | name of index to be created

    var type = "type_example"; // String | type of index, should be Simple_Search or Ecommerce

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    this.service.addIndex(name, type, API_KEY).subscribe(
      function callback(data) {
        console.log("Api called successfully");
        console.log(data);
      }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **name** | **String**| name of index to be created | 
 **type** | **String**| type of index, should be Simple_Search or Ecommerce | 
 **API_KEY** | **String**| API_KEY for authentication | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="addObject"></a>
# **addObject**
> Object addObject(indexName, API_KEY, _object)

first perform this [**step**](#mandatoryStep)

This will add an object to the given index.

It rquire a json object which we want to add.

### Example


```typescript
import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {

    var indexName = "indexName_example"; // String | name of index

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    var _object = {
      "objectID": 1,
      "title": "Sample title",
      "content": "Sample content"
    }; // Object | This is the single object to be add in index.

    this.service.addObject(indexName, API_KEY, _object).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **indexName** | **String**| name of index | 
 **API_KEY** | **String**| API_KEY for authentication | 
 **_object** | [**Object**](Object.md)| This is the single object to be add in index. | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="addObjects"></a>
# **addObjects**
> Object addObjects(indexName, API_KEY, objectsList)

first perform this [**step**](#mandatoryStep)

This will add an array of objects to the given index.

It rquire a json array of objects which we want to add.

### Example
```javascript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {

    var indexName = "indexName_example"; // String | name of index

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    // [Object] | This is a list of objects to be add in index.
    var objectsList =  [
      {
          "objectID": 2,
          "title": "Sample title",
          "content": "Sample content"
      },
      {

          "objectID": 3,
          "title": "Sample title",
          "content": "Sample content"
      }
    ]
    this.service.addObjects(indexName, API_KEY, objectsList).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **indexName** | **String**| name of index | 
 **API_KEY** | **String**| API_KEY for authentication | 
 **objectsList** | **[Object]**| This is the single object to be add in index. | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="copyIndexConfig"></a>
# **copyIndexConfig**
> Object copyIndexConfig(API_KEY, src, dest)

first perform this [**step**](#mandatoryStep)

Copy Index configuration from one index to another

Copy Index Configuration, provide src and dest for copying index configuration

### Example
```javascript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    var src = "src_example"; // String | Source Index

    var dest = "dest_example"; // String | Target Index

    this.service.copyIndexConfig(API_KEY, src, dest).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **API_KEY** | **String**| API_KEY for authentication | 
 **src** | **String**| Source Index | 
 **dest** | **String**| Target Index | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="deleteIndex"></a>
# **deleteIndex**
> Object deleteIndex(index, API_KEY)

first perform this [**step**](#mandatoryStep)

Delete Index

Delete Index, provide name

### Example
```javascript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {

    var index = "index_example"; // String | name of index to be deleted

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    this.service.deleteIndex(index, API_KEY).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **index** | **String**| name of index to be deleted | 
 **API_KEY** | **String**| API_KEY for authentication | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="deleteObject"></a>
# **deleteObject**
> Object deleteObject(indexName, API_KEY, objectID)

first perform this [**step**](#mandatoryStep)

This will delete the object with given object id

this require an objectID of object to be deleted

### Example
```typescript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {

    var indexName = "indexName_example"; // String | name of index

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    var objectID = "objectID_example"; // String | objectId of the object to be deleted

    this.service.deleteObject(indexName, API_KEY, objectID).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **indexName** | **String**| name of index | 
 **API_KEY** | **String**| API_KEY for authentication | 
 **objectID** | **String**| objectId of the object to be deleted | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="generateEvent"></a>
# **generateEvent**
> Object generateEvent(indexName, API_KEY, type, _object)

first perform this [**step**](#mandatoryStep)

This will generate an event.

event type should be provided and it shoulb be click.

### Example
```typescript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {
    
    var indexName = "indexName_example"; // String | name of index

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    var type = "type_example"; // String | type of the event

    this.service.generateEvent(indexName, API_KEY, type, {
      "clickedByUser": "",
      "objectClickedOn": ""
    })
    .subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **indexName** | **String**| name of index | 
 **API_KEY** | **String**| API_KEY for authentication | 
 **type** | **String**| type of the event | 
 **_object** | [**Object1**](Object1.md)| This is the single object to be add in index. | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="getAllObjects"></a>
# **getAllObjects**
> Object getAllObjects(index, API_KEY)

first perform this [**step**](#mandatoryStep)

Get All objects stored in index

Get All objects stored in index, limit is 1000

### Example
```javascript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {

    var index = "index_example"; // String | 

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    this.service.getAllObjects(index, API_KEY).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **index** | **String**|  | 
 **API_KEY** | **String**| API_KEY for authentication | 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

<a name="getAllIndices"></a>
# **getAllIndices**
> Object getAllIndices(index, API_KEY)

first perform this [**step**](#mandatoryStep)

Get list of all indices

Get list of all indices with number of queries and records

### Example
```javascript

import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {

    var API_KEY = "API_KEY_example"; // String | API_KEY for authentication

    this.service.getAllIndices(API_KEY).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **API_KEY** | **String**| API_KEY for authentication | 

### Return type

**Array**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


<a name="searchQuery"></a>
# **searchQuery**
> Object searchQuery(indexName, query, API_KEY, size, userToken, searchParameters)

first perform this [**step**](#mandatoryStep)

Returns a Search Results in an object.
each result is termed as a hit.
stored in an array accessed by data['hits']['hits'], assuming search object is named as data.

### Example
```javascript
import { SearchService } from 'universal-search-engine-angular'

export class DemoSearchComponent implements OnInit{

  constructor(private service: SearchService) {}
  ngOnInit(): void {
    var indexName = "indexName_example"; // String | name of index

    var query = "query_example"; // String | Query to be searched

    var API_KEY = "API_KEY_example"; // String | API KEY for authentication

    this.service.searchQuery(indexName, query, API_KEY).subscribe(
       function callback(data) {
            console.log("Api called successfully");
            console.log(data);
       }
    ) 
  }
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **indexName** | **String**| name of index | 
 **query** | **String**| Query to be searched | 
 **API_KEY** | **String**| API KEY for authentication | 
 **size** | **Number**| maximum number of results to be returned | [optional] 
 **userToken** | **String**| userToken for personalization | [optional] 
 **searchParameters** | [**SearchParameters**](SearchParameters.md)| The user to create. | [optional] 

### Return type

**Object**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

