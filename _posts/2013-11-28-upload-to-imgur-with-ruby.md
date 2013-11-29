---
layout: post
---

# Uploading an image to imgur.com using ruby 

1. Go to <http://www.imgur.com> and create an account.
2. Go to <https://api.imgur.com/oauth2/addclient>
	1. Give a name to your app
	2. Select **Anonymous usage without user authorization** in _Authorization type_.
	3. Provide your email.
	4. Give a description for the app.
	5. Fill in the captcha.
	6. Click _Submit_.  
![register 1]({{site.url}}/images/2013-11-28-1.png)
![register 2]({{site.url}}/images/2013-11-28-2.png)
3. You will get an email with your **client_id** and your **client_secret**.
4. If you intend to upload anonymously, you only need to use your client_id.
5. Make a POST request to <https://api.imgur.com/3/upload.json> with the following properties:
	1. A header called `Authorization` with the value `Client-ID client_id`.
	2. A parameter called `image` with the image data encoded in Base64.


Example in ruby (replace `client_id` with your client_id ):

{% highlight ruby %}
#!/usr/bin/ruby

require 'net/http'
require 'uri'
require 'base64'
require 'json'

filename = "image.png"

imagedata = Base64.encode64(File.read(filename))

url = "https://api.imgur.com/3/upload.json"
params = {image: imagedata}

uri = URI.parse(url)

https = Net::HTTP.new(uri.host, uri.port)
https.use_ssl = true

request = Net::HTTP::Post.new(uri.path)
request["Authorization"] = "Client-ID client_id"
request.set_form_data(params)

response = https.request(request)

hash = JSON.parse(response.body)
link = hash["data"]["link"]

pust hash
puts link
{% endhighlight %}
