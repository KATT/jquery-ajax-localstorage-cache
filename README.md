# About
jquery-ajax-localstorage-cache is a plugin built for jQuery (>1.5.1) and localStorage. It's a fork from the [jStorage-dependent original](https://github.com/nectify/jquery-ajax-jstorage-cache). It provides a client-side cache AJAX responses intended to save bandwith and time.

# How to use

## Parameters
```javascript
$.ajaxLocalstorageCache.defaults = {
  localCache: false,
  cacheTTL: 5,
  isCacheValid: function(/* requestOptions */) {
    return true
  },
  isResponseValid: function(/* responseData */) {
    return true
  },
  cachePrefix: 'ajaxcache_'
};
```

You can either send the parameters when doing `$.ajax()` or overriding them globally, e.g. `$.ajaxLocalstorageCache.defaults.localCache = true;`

On your AJAX request you get 4 new parameters :

* localCache
	* Turn localCache on/off
	* Default: false
* cacheTTL
    * time in hours the entry should be valid.
    * only for this specific ajax request
    * Default : 5 hours
* cachePrefix
	* Default: ajaxcache_
* cacheKey
	* CacheKey is the key that will be used to store the response in localStorage. It allow you to delete your cache easily with the localStorage.removeItem() function.
	* Default: URL + TYPE(GET/POST) + DATA
* isCacheValid
	* This function must return true or false. On false, the cached response is removed.
	* Default: null
* isResponseValid
	* This function must return true or false. On false, the response will not be cached.
	* Default: null

## Notes

* You can delete the cache by using ```localStorage.clear()```.
* Note that you can pre-load content with this plugin. You just have do to the same AJAX request without a success callback and the same cacheKey.

# License

This project is distributed under Apache 2 License. See LICENSE.txt for more information.
