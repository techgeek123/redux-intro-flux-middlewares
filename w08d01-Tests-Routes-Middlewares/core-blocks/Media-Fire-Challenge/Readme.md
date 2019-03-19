# MediaFire API

This assignment contains only a programming part. The service used is http://www.mediafire.com/. Before starting, the student has to create an account at the service, do this using password authentication. Once logged in, click on your user logo and select Account settings then select Developers and create a new application. You will need the App ID and API Key for in the code which you will write for this exercise. The RESTful API of mediafire is described on this webpage http://www.mediafire.com/developers/core_api/1.4/getting_started/ , read trough the description of the interface. (You can also find an SDK from other parts of the developer documentation, but you cannot use it for this exercise since it hides all HTTP communication, which is exactly what this exercise is about.)



## Release0:
- You are expected to create a method/function/… with four string parameters (APP_id, API_key, email, password) this method/function/… should return an object/struct/type/… from which the following information can be obtained:
	- Birth date
	- Display name
	- Email
	- First name
	- Last name
	- Gender

- You need to make two API calls. The first one will log you in to the mediafire service. See [user documentation](http://www.mediafire.com/developers/core_api/1.4/user/#get_session_token)


## Release1:
- Information returned by that call will be used in the next call to [get user info](http://www.mediafire.com/developers/core_api/1.4/user/#get_info)
- You will communicate with the service using JSON.

- Do not use simple string concatenation to create URLs ([Percent encoding](https://en.wikipedia.org/wiki/Percent-encoding) of parameters is handled automatically in many libraries )

## Release2:
- You have to test your implementation with weird passwords like a ``~'goöd\" #p@ssw0rd世界 ``(remember to escape this properly if you hard code your password in your program "``a ~'goöd\\\" #p@ssw0rd世界``")

- You must use the library management tools which are available for the language you choose (Java: maven, Python: pip/easy_install, etc.) if you are using external libraries. If you are using a rare programming language (ask the teacher), add used external libraries to the repository.
Returning the task

- Clone the teacher’s repository in yousource ```git@yousource.it.jyu.fi:ties456-2015/week37.git``` and add the teacher as a collaborator. Put the parts you created yourself to your git repository and add the teacher (username ``miselico`` as a collaborator to your repository) Include a class with a ‘main function’ or equivalent to test your class. Use of dependency injection and writing proper unit tests is encouraged, but not obligated.