* `200 ok` - The `GET`, `PUT`, `DELETE` request was successful, the resource(s) itself is returned as `JSON`
* `201 Created` - The `POST` request was successful and the resource is returned as `JSON`
* `400 Bad Request` - A required attribute of the API request is missing, e.g. the title of an isssue is not given
* `401 Unanthorized` - The user is not authenticated, a valid user token is necessary
* `403 Forbidden` - The request is not allowed, e.g. the user is not allowed to delete a project
* `404 Not Found` - A resource could not be accessed, e.g. an ID for a resource could not be found
* `405 Method Not Allowed` - The request is not supported
* `409 Conflict` - A conflicting reosurce already exists, e.g. creating a project with a name that already exists
* `500 server Error` - While handing the request something wnet wrong on the server side
