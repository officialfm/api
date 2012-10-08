# oEmbed

[oEmbed](http://www.oembed.com) is a format for allowing an embedded representation of a URL on third party sites. It allows a website to display embedded content (such as photos or videos) when a user posts a link to that resource, without having to parse the resource directly.
You can use official.fm track and playlist URL’s to get a players embed code.
 
## official.fm implementation

To request embed code, you have to use our API oEmbed endpoint.

We support JSON (default) and XML as format responses.

#### API endpoints

    http://official.fm/services/oembed.FORMAT?url=...
    http://official.fm/services/oembed?format=FORMAT&url=... 

You can request embed codes for tracks and playlists by using our URL scheme.

#### URL scheme

    http://official.fm/tracks/*
    http://official.fm/playlists/* 

 
## Examples

**JSON Request**

http://official.fm/services/oembed.json?url=http://official.fm/tracks/npTR

Response:

	{
		"type":"rich",
		"version":"1.0",
		"title":"Wiz Khalifa - Work Hard Play Hard (Remix ft. Lil Wayne & Young Jeezy)",
		"author_name":"Wiz Khalifa",
		"provider_name":"Official.fm",
		"provider_url":"http://official.fm/",
		"width":400,
		"height":40,
		"html":"<iframe width='400' height='40' src='http://official.fm/player?width=400&height=40&feed=http%3A%2F%2Fofficial.fm%2Ffeed%2Ftracks%2FnpTR.json' frameborder='0'></iframe>"
	}
                  

**XML Request**

http://official.fm/services/oembed.xml?url=http://official.fm/playlists/1rp7

Response:

    <oembed>
    	<type>rich</type>
    	<version>1.0</version>
    	<title>Macadelic</title>
    	<author_name>Mac Miller</author_name>
    	<provider_name>Official.fm</provider_name>
    	<provider_url>http://official.fm/</provider_url>
    	<width>400</width>
    	<height>40</height>
    	<html>
    		<iframe width='400' height='40' src='http://official.fm/player?width=400&height=40&feed=http%3A%2F%2Fofficial.fm%2Ffeed%2Fplaylists%2F1rp7.json' frameborder='0'>
    		</iframe>
    	</html>
    </oembed>

## Wordpress integration

Wordpress has supported oEmbed since Version 2.9. 

It has really simplified video and audio embeds in your blog post.

To add official.fm as a whitelist oEmbed provider to your blog, just add this line at the top of "functions.php" (in your theme folder) after <?php :

    wp_oembed_add_provider('http://official.fm/*', 'http://official.fm/services/oembed/'); 

Once done, simply enter the plain text URL of an official.fm track or playlist somewhere within your blog post and it will automatically turn into an official.fm embedded player. Magic!

    http://official.fm/tracks/npTR 

By default, small player with a 100% width will be displayed but you can also adjust player width by wrapping your URL in the an [embed] shortcode:

    [embed width="200px"]http://official.fm/tracks/npTR[/embed] 

or

    [embed width="50%"]http://official.fm/tracks/npTR[/embed] 
