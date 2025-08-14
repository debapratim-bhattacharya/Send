## Getting started with Moosend API

Before making use of our API, please read the following carefully to get you started.

## Making API Requests

Both API requests and responses have a format the data is expected to be sent or returned.

Requests consist of a URL that specifies which operation to also call, a query string and usually a request stream as well, which specify parameters for the call. For each request there is a syntax pattern for the URL that must be followed for the system to understand your intension. You may find the appropriate pattern for each call in the “Access URLs” sections in our API Documentation pages.

Parameters in the query string or the request stream should be specified in a format like:

name1=value1&name2=value2&name3=value3&...

As you have probably noticed, each name-value pair is separated by a & character. Note also that special characters in values should be URL-encoded. There are built-in URL-encoding functions in all major programming languages like C# and PHP. Please refer to each language’s documentation for more information.

The request must also contain information about how you would like the response to be formatted. There are currently two available formats for getting a response: **xml** and **json**. You have to specify the format in every API call as an extension in the URL.

So let’s summarize all above with an example request URL and a couple of hypothetical parameters:

Example requesting response in xml format:

`http://api.moosend.com/v3/somepath/testmethod.xml?param1=value1&m2=value2+with+special+chars+like+@`

Example requesting response in json format:

`http://api.moosend.com/v3/somepath/testmethod.json?param1=value1&m2=value2+with+special+chars+like+@`

Note also that you must set the correct accept header in your application’s request in order to retrieve the response data in the expected format.

For xml response you must set the accept header to: **application/xhtml+xml,application/xml**

For json response you must set the accept header to: **application/json**

## Authentication

All API calls require authentication. This is essential for the API to identify which user is making the call so that appropriate results will be returned, as well as for security reasons.

Authentication is achieved through the use of an API key. This is a unique key for each account in our system. You can get your API key from the settings page in your account. Please keep your API key safe to prevent any unauthorized access. Once you obtain your API key, you will have to use it in every API call you make. The API key must always be specified as a parameter in the query string of the requesting URL, as in the example below:

`http://api.moosend.com/v3/campaigns/create.xml?apikey=YOUR_API_KEY`

You may find your API Key or generate a new one in the respective section under the Settings Menu.

## Request Methods

There are 3 request methods that you will have to use in order to make full use of our API: GET, POST and DELETE. You must set your application to make each API call using the appropriate request method, which is explicitly specified in our API documentation pages for each call. Let us explain how these methods should be used:

**GET:** Used for retrieving data from your account in our system. All request parameters in this case are expected to be found in the request URL, in a format specified explicitly for each API call. You can find detailed information on how to specify parameters for each call in our API documentation pages. You may test a GET request in a web browser, by entering the URL in the address bar. Don't forget to include your API key parameter in the query string!

**POST:** Used for sending information to our system in order to modify data in your account. In this case request parameters should be specified in the request stream. Only authentication and response format are usually expected to be found in the URL, unless differently specified in the “Access URLs” section of our API Documentation pages. Currently, the API accepts only URL-encoded data in the request stream, which is the same format as the one expected for parameter values in the query string. Note also that the content-type header of the request to be made should be “application/x-www-form-urlencoded”.

**DELETE:** Used for deleting information from your account. No more different from POST regarding its use.

Below is an example of a _POST_ request:

Request URL:

`http://api.moosend.com/v3/campaigns/create.xml?apikey=YOUR_API_KEY`

Request Stream:

_(assumes hypothetical parameters: Name = New campaign, Subject = Some cool subject, SenderEmail =_ [<i>info@example.com</i>](https://mailto:info@example.com)_, WebLocation =_ [<i>http://example.com/home/newsletter</i>](http://example.com/home/newsletter)_, MailingListID = 01234567-89ab-cdef-0123-456789abcdef)_

`Name=New+campaign&Subject=Some+cool+subject&SenderEmail=info@example.com& WebLocation=http://example.com/home/newsletter&MailingListID=01234567-89ab-cdef-0123-456789abcdef`

## Changelog

- Added HasExternalDoubleOptIn property in [Adding subscribers](https://jsapi.apiary.io/previews/moosendapp/reference/subscribers/add-or-update-subscribers/adding-subscribers)
    
- Added HasExternalDoubleOptIn property in [Adding multiple subscribers](https://jsapi.apiary.io/previews/moosendapp/reference/subscribers/add-or-update-subscribers/adding-multiple-subscribers)
    
- Added HasExternalDoubleOptIn property in [Updating a subscriber](https://jsapi.apiary.io/previews/moosendapp/reference/subscribers/add-or-update-subscribers/updating-a-subscriber)
