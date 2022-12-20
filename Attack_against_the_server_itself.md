
# SSRF attacks against the server itself

In an SSRF attack against the server itself, the attacker induces the application to make an HTTP request back to the server that us hostinghg the application, via its loopback network interface. This will typically involve supplying a URL with hostname like 127.0.0.1 or localhost.
**Example:** consider a shopping application that lets the user view whether an item is in stock in a particular store. to provide the stock information, the application must query various back-end REST APIs, dependent on the product and the store in question. the function is implemented by passing the URL to the relevant back-end API endpoint via a front-end HTTP request.

```sh
POST /product/stock HTTP/1.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 118

stockApi=http://stock.weliketoshop.net:8080/product/stock/check%3FproductId%3D6%26storeId%3D1
```
This causes the server to make a request to the specified URL, retrieve the stock status, and return this to the user. In this situation, an attacker can modify the request to specify a URL local to the server itself. For Example:
```sh
POST /product/stock HTTP/1.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 118

stockApi=http://localhost/admin
```
Here, the server will fetch the content of the /admin URL and return ot to the user.
