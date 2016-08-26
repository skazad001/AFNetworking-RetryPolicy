<h3 align="center">
  <img src="https://raw.githubusercontent.com/kubatru/AFNetworking-RetryPolicy/master/Images/logo.png” alt=“Logo” height=“850”/>
</h3>

# AFNetworking+RetryPolicy
- If the request timed out, you usually have to call the request again by yourself. **AFNetworking+RetryPolicy** handles that for you.
 
- Adds the ability to set the retry interval, retry count and progressive (uses power rule e.g. interval = 3 -> 3, 9, 27 etc.). `failure` is called no earlier then `retryCount` = 0, only `fatalStatusCodes` finishes the request earlier.

### Allows you to:
- [x] How many times to try.
- [x] Time interval between attempts in seconds.
- [x] The next attempt will always take more time then the previous one. (Progressive)

## Installation
**Category requires [AFNetworking](https://github.com/AFNetworking/AFNetworking) 3.0 and above**

- Add the **AFNetworking+RetryPolicy** category to your project as a regular library.

## Usage
- E.g. Simple `GET` request will look like this.
- You can also turn on the logging in the category to see what happens.

```objective-c
	AFHTTPSessionManager *manager = [AFHTTPSessionManager new];
    [manager GET:@"foo" parameters:nil progress:nil success:^(NSURLSessionDataTask *task, id responseObject) {
        NSLog(@"%@", responseObject);
        
    } failure:^(NSURLSessionDataTask *task, NSError *error) {
        NSLog(@"%@", error.localizedDescription);
        
    } retryCount:5 retryInterval:2.0 progressive:false fatalStatusCodes:@[@401, @403]];
```

## Author
- This library is open-sourced by [Jakub Truhlar](http://kubatruhlar.cz).
    
## License
- Like(:+1:) [AFNetworking](https://github.com/AFNetworking/AFNetworking), this category is under the MIT License (MIT)
Copyright © 2016 Jakub Truhlar