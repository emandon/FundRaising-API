#Authentication

Every call to the iBanFirst Fundraising API must be authenticated, which must be done by adding a custom HTTP header (X-WSSE) with your username and secret. This section contains detailed instructions on how to create valid headers for the Suite fundraising API.
All API request must be made over HTTPS. Calls made over plain HTTP will fail. You must authenticate for all requests.
X-WSSE Format. Also, as this API is made for partners, you will have to provide an additional token to certify the request.

##Creating the header

The header has the following format, usually a single HTTP header line which we broke down into multiple lines for easier readability:

~~~
X-WSSE: UsernameToken
	Username="customer001",
	PasswordDigest="+QpstwYoZeToelOvVaObTdRdEZs=",
	Nonce="d36e3162829ed4c89851497a717f",
	Created="2014-03-20T12:51:45Z"
~~~

The following sections describe each component in detail:

* X-WSSE : Name of the [HTTP](http://en.wikipedia.org/wiki/HTTP) header we use for authenticating the request.
* UsernameToken : Authentication method. The X-WSSE header must contain a UsernameToken as we only support token-based authentication.
* Username : Field containing the username you were provided during onboarding.
* PasswordDigest : Field containing the hashed token which will prove the authenticity of your request. It is essential that you recompute this hash for every request as a hash is only valid for a certain period of time, and then it expires.
* Nonce : A random value used to make your request unique so it cannot be replicated by any other unknown party.
* Created : Field containing the current UTC, GMT, ZULU timestamp (YYYY-MM-DDTHH:MM:SSZ) according to the [ISO8601](http://fr.wikipedia.org/wiki/ISO_8601) format, *e.g. 2014-03-20T12:51:45Z*.

##Computing the Password Digest

Computing the password digest involves 5 simple steps:

* Get a randomly generated 16 byte Nonce formatted as 32 hexadecimal characters.
* Get the current Created timestamp in ISO-8601 format.
* Concatenate the following three values in this order: nonce, timestamp, secret.
* Calculate the SHA-1 hash value of the concatenated string, and make sure this value is in binary format! Some languages, like PHP, output hexadecimal hash by default. You may need to use special methods to obtain hexadecimal hashes in different languages or even convert byte to hex values by hand (see the sample codes below for more information).
* Apply a Base64 encoding to the resulted hash to get the final PasswordDigest value.

##Exemple of creating the X-WSSE header with PHP

Here is a sample code that you can use to make your X-WSSE header, or just in a way of understanding the process.

~~~php
<?php
// Login informations
$username = "YourUserName" ;			// The username used to authenticate
$password = "secret" ;				// The password used to authenticate
$nonce = "" ;					// The nonce
$nonce64 = "" ;					// The nonce with a Base64 encoding
$date = "" ;					// The date of the request, in  ISO 8601 format
$digest = "" ;					// The password digest needed to authenticate you
$header = "" ; 					// The final header to put in your request

// Making the nonce and the encoded nonce
$chars = "0123456789abcdef";
for ($i = 0; $i < 32; $i++) {
    $nonce .= $chars[rand(0, 15)];
}
$nonce64 = base64_encode($nonce) ;

// Getting the date at the right format (e.g. YYYY-MM-DDTHH:MM:SSZ)
$date = gmdate('c');
$date = substr($date,0,19)."Z" ;

// Getting the password digest
$digest = base64_encode(sha1($nonce.$date.$password, true));

// Getting the X-WSSE header to put in your request
$header = sprintf('X-WSSE: UsernameToken Username="%s", PasswordDigest="%s", Nonce="%s", Created="%s"',$username, $digest, $nonce64, $date);
~~~

##Special characters

When sending data to our API, you may notice that certain characters are forbidden for security purpose. Those characters are forbidden in route parameters, optional (query) parameters and JSON bodies.

Here is the list of forbidden characters :
`& (ampersand) < (open chevron) > (close chevron) % (percentage) ? (question mark) \ (anti-slash) / (slash) | (pipe)`

##Adding the partner token to the authentication

Albeit using the WSSE security to do request for a user to the API, you must authenticate as a partner. 

To authenticate, you will be granted a partner token, a 16-character hexadecimal string, that will be mandatory to execute requests on the API. 

This partner token must be given by the “X-WSSE-REQUESTED-BY” HTTP header.

~~~
X-WSSE-REQUESTED-BY: c6da61fcff03c20b
~~~

If you do not provide this header doing requests on the API, the request will be rejected.
