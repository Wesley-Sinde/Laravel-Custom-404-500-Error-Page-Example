# Laravel 9 Custom 404, 500 Error Page Example

Laravel 9 custom 404, 500 error page example; In this tutorial, we will learn how to create/build custom error pages in laravel 9 apps.

Usually, laravel 9 display default error page 404, 500. But if you want to design of this pages. So, you can do it. This tutorial will guide you to step by step from scratch for how to create custom 404, 500 error pages in laravel

Laravel 9 Custom 404, 500 Error Page Example
Follow the following to create and use custom 404 and 500 page in laravel 9 apps:

* Create 404 View File
* Create 500 View File
* Modify Exceptions Handler
## 1: Create 404 View File
Visit to resources/views folder and create a folder named errors.

Then inside this errors folder, create a file called 404.blade.php. So the location of our 404 page is resources/views/errors/404.blade.php.

resources/views/errors/404.blade.php

```html
<!DOCTYPE html>
<html>
<head>
    <title>Page Not Found</title>
</head>
<body>
This is the custom 404 error page.
</body>
</html>
```
## 2: Create 500 View File
Visit to resources/views folder and create a folder named errors.

Then inside this errors folder, create a file called 500.blade.php. So the location of our 500 page is resources/views/errors/500.blade.php.

resources/views/errors/500.blade.php
```html
<!DOCTYPE html>
<html>
<head>
    <title>Page Not Found</title>
</head>
<body>
This is the custom 500 error page.
</body>
</html>
```
## 3: Modify Exceptions Handler
Now, navigate to app/Exceptions and open Handler.php file and find the render() method. Then modify the render() method only as follow:


```php
public function render($request, Exception $exception)
{
    if ($this->isHttpException($exception)) {
        if ($exception->getStatusCode() == 404) {
            return response()->view('errors.' . '404', [], 404);
        }
    }
    return parent::render($request, $exception);
}
```
as well as render 500 error page in this file as follow:


```php
public function render($request, Exception $exception)
{
    if ($this->isHttpException($exception)) {
        if ($exception->getStatusCode() == 404) {
            return response()->view('errors.' . '404', [], 404);
        }
        if ($exception->getStatusCode() == 500) {
            return response()->view('errors.' . '500', [], 500);
        }
    }
    return parent::render($request, $exception);
}
```
# Conclusion
Laravel 9 create custom error page example, we have learned how to create custom page for 404, 500 error in laravel apps. As well as how to use them.
