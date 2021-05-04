# universal-search-engine-angular
UniversalSearchEngine - Typescript angular client for universal-search-engine-angular
universal search engine api

## Installation


#### npm

Then install it via:

```shell
npm install universal-search-engine-angular --save
```


You should now be able to import from `'universal-search-engine-angular'` in javascript files from the directory you ran the last command above from.


## Getting Started

#### Mandatory Step
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

Next, in your component.ts file add this
```typescript
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

## Documentation for API Endpoints

All URIs are relative to *https://search-engine-walkover.el.r.appspot.com*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*UniversalSearchEngine.SearchService* | [**addIndex**](docs/SearchService.md#addIndex) | **POST** /addIndexByApi | Add Index By Api
*UniversalSearchEngine.SearchService* | [**addObject**](docs/SearchService.md#addObject) | **POST** /add/{index_name} | This will add an object to the given index.
*UniversalSearchEngine.SearchService* | [**addObjects**](docs/SearchService.md#addObjects) | **POST** /bulkadd/{index_name} | This will add an array of objects to the given index.
*UniversalSearchEngine.SearchService* | [**copyIndexConfig**](docs/SearchService.md#copyIndexConfig) | **POST** /copyIndexConfig | Copy Index configuration from one index to another
*UniversalSearchEngine.SearchService* | [**deleteIndex**](docs/SearchService.md#deleteIndex) | **DELETE** /deleteIndexByApi | Delete Index
*UniversalSearchEngine.SearchService* | [**deleteObject**](docs/SearchService.md#deleteObject) | **DELETE** /delete/{index_name} | This will delete the object with given object id
*UniversalSearchEngine.SearchService* | [**generateEvent**](docs/SearchService.md#generateEvent) | **POST** /event/{index_name} | This will generate an event.
*UniversalSearchEngine.SearchService* | [**getAllObjects**](docs/SearchService.md#getAllObjects) | **POST** /getAllObjects | Get All objects stored in index. 
*UniversalSearchEngine.SearchService* | [**getAllIndices**](docs/SearchService.md#getAllIndices) | **POST** /getAllIndices | Get All indices
*UniversalSearchEngine.SearchService* | [**searchQuery**](docs/SearchService.md#searchQuery) | **POST** /search/{index_name} | 


## Documentation for Models

 - [UniversalSearchEngine.ModelObject](docs/ModelObject.md)
 - [UniversalSearchEngine.Object1](docs/Object1.md)
 - [UniversalSearchEngine.SearchParameters](docs/SearchParameters.md)


## Documentation for Authorization

 All endpoints do not require authorization.

