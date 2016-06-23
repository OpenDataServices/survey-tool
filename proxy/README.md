PHP Proxy File by ESRI
===========================

A PHP proxy that handles support for
* Accessing cross domain resources
* Requests that exceed 2048 characters
* Accessing resources secured with token based authentication.
* [OAuth 2.0 app logins](https://developers.arcgis.com/en/authentication).
* Enabling logging
* Both resource and referer based rate limiting

See [full instructions and original code] (https://github.com/carlosiglesias/resource-proxy/tree/bump/PHP) for details

Function isAllowedApplication at proxy.php has been adapted to allow http://domain.com/* wildcards for referers using regexp, as the survey has multiple and unpredictable http://surveydomain.com/surveyKey referals and otherwise it will be impossible to grant access to all of them unless using * wildcard option that is not recommended for final deployment given security constraints.

## Instructions

* Test that the proxy is installed and available:
```
http://[yourmachine]/proxy/proxy.php?ping
```
* Test that the proxy is able to forward requests directly in the browser using:
```
http://[yourmachine]/proxy/proxy.php?http://example.org
```

## Folders and Files

The proxy consists of the following files:
* proxy.config: This file contains the [configuration settings for the proxy](../README.md#proxy-configuration-settings). This is where you will define all the resources that will use the proxy.
* proxy.php: The actual proxy application. In most cases you will not need to modify this file.

Other useful files in the repo:
* .htaccess: This file is an example Apache web server file which includes recommended file filtering.
* proxy-verification.php: Useful testing page if you have installation problem.

Files created by the proxy:
* proxy.sqlite: This file is created dynamically after proxy.php runs.  This file supports rate metering.
* proxy_log.log: This file is created when the proxy.php runs (and logging is enabled). Note: If you do not have write permissions to this directory this file will not be created for you. To check for write permissions run the proxy-verification.php.

## Requirements

* PHP 5.4.2 (recommended)
* cURL PHP extension
* OpenSSL PHP extension
* PDO_SQLITE PDO PHP extension


##Licensing

Copyright 2014 Esri

Licensed under the Apache License, Version 2.0 (the "License");
You may not use this file except in compliance with the License.
You may obtain a copy of the License at
http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" basis, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for specific language governing permissions and limitations under the license.
