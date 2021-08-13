# RestFetch

The `RestFetch` interface is a wrapper over Javascript's `fetch` that automatically constructs a chain of functions that perform `fetch` based upon hyperlink data. This enables a complete interface to a compatible RESTful API. A compatible API must return JSON that essentially follows this pattern:
```json
{
	...,
	"links": [
		{
			"rel": "This becomes the function name in the JS object",
			"method": "HTTP methods supported, separated by a |",
			"href": "address to query",
			"[postData]": "Any string or object representing a template to send back in POST requests"
		},
		...
	]
}
```
Every link will be translated into a function on the returned object of `RestFetch`, based upon method and rel string. For example, using `RestFetch` may look like this:
```javascript
let data = await $_.RestFetch('/api/', 'portfolio', err_callback);
let settings = await data.getSettings(); 
let postData = Object.assign({}, settings.postAddressPostData);
postData.address = '123 New Address Lane';
await settings.postAddress(postData);
```


# LICENSE

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

In jurisdictions that recognize copyright laws, the author or authors of this software dedicate any and all copyright interest in the software to the public domain. We make this dedication for the benefit of the public at large and to the detriment of our heirs and successors. We intend this dedication to be an overt act of relinquishment in perpetuity of all present and future rights to this software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to http://unlicense.org/
