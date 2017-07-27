# loklak_jlib_api
[![Build Status](https://api.travis-ci.org/loklak/loklak_jlib_api.svg)](https://travis-ci.org/loklak/loklak_jlib_api)

This is the Loklak Java API.
One Library to find them, One Library to bring them all.

## What is loklak?
Loklak server scrapes data from multiple social networking websites, primarily from Twitter. The 
scraped data is open and can be accessed by anyone without the need of an API key!!! For more 
please visit [http://loklak.org](http://loklak.org).

## What can I do with it?
You can anonymously use the data provided by Loklak server using this library. Currently it 
supports the following API endpoints:
* [search](http:loklak.org/api.html#search)
* [suggest](http:loklak.org/api.html#suggest)
* [peers](http:loklak.org/api.html#peers)
* [hello](http:loklak.org/api.html#hello)
* [crawler](http:loklak.org/api.html#crawler)
* [status](http:loklak.org/api.html#status)
* [user](http:loklak.org/api.html#user)
* [apps](http:loklak.org/api.html#apps)
* [push](http:loklak.org/api.html#push)

## Dependencies
It depends on joda and json libraries which are included in android by default.
If you want to use this library in an android project, you therefore have zero dependencies.
If you want to use this library in any other java project, just include the jar files in the lib folder.

## How to build the library
After successful build using ```maven```, jar file can be found in ```target``` folder. Building 
and testing in command line and different IDEs:
* Using command line:
  ```bash
  $ mvn clean package # to build
  $ mvn clean compile test # to run unit-test
  ```
  
* In eclipse:
    * Right click on *Project name* in package explorer > Run as > Maven Build ... > 
    Write ```clean package``` in *goals*. Use the created run configuration to generate the jar 
    file.
    * Right click on *Project name* > Run as > Maven Test
    
* In IntelliJ IDEA:
    * View > Tool Windows > Maven Projects > Lifecycle > Select the required lifecycle.

## How to use it?
Its as simple as:
```java
public class LoklakApiUse {
    
    public static void main(String[] argv) {
        String baseUrl = "https://api.loklak.org";
        // API methods are generated by the library.
        LoklakAPI loklakApi = APIGenerator.createApiMethods(LoklakAPI.class, baseUrl);
        
        // using the hello API endpoint, request url: http://api.loklak.org/api/hello.json
        JSONOBject helloReply = loklakApi.hello(); // use the required API endpoint with parameters
        System.out.println(helloReply.toString());
        
        // similarly search API endpoint, request url: https://api.loklak.org/api/search.json?q=fossasia
        JSONObject searchReply = loklakApi.search("fossasia");
        System.out.println(searchReply.toString());
    }
}
```