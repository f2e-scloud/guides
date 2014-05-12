Status Code
===========

**Author**: gejiawen
**Email**: gejiawen@baidu.com
**Desp**:
>The normal structure of returned value as follows:
> ```javascript
> {
    'code': xxx,
    'message': xxx,
    'data': xxx
> }
> ```
> Maybe some others properties were added.


*Here are some code for scenario in my mind*:

* `200 Ok`
    * The `GET`, `PUT`, `DELETE` request was successful, the resource(s) itself is returned as `JSON`
* `201 Created`
    * The `POST` request was successful and the resource is returned as `JSON`
* `400 Bad Request`
    * A required attribute of the API request is missing, e.g. the title of an isssue is not given
* `401 Unanthorized`
    * The user is not authenticated, a valid user token is necessary
* `403 Forbidden`
    * The request is not allowed, e.g. the user is not allowed to delete a project
* `404 Not Found`
    * A resource could not be accessed, e.g. an ID for a resource could not be found
* `405 Method Not Allowed`
    * The request is not supported
* `409 Conflict`
    * A conflicting reosurce already exists, e.g. creating a project with a name that already exists
* `500 server Error`
    * While handing the request something wnet wrong on the server side

--------------

*The interface of http*:

* 前端将会有一个统一的入口，前端调用的所有的接口都是通过此入口（具体实现见**`httpfactory`**）
* `httpfactory` 会对不同的 `http method` 做判断，对不同的 `status code` 做判断
* `httpfactory` 中还会建立简单的错误处理和报警机制

--------------

*The interface of observer*:

* 当前端业务逻辑划分为多个模块时，采用p/b进行各模块间的通信交互
* 具体实现见**`config.ob`**

--------------

*The interface of global store*:

* 我们不推荐将全局变量直接存在window下，因为这些可能会造成全部变量污染等弊端
* 我们实现一个服务，采用一个封边的作用域来保存所有的全局或者需要被临时保存的变量。此作用域的生命周期直到浏览器(页面)关闭
* 具体实现见**`service.store`**