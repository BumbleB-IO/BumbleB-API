<p align="center">
<img align="center" src="api_bumbleb_header.gif" width="100%" alt="API BumbleB logo"/>
</p>


# BumbleB API Documentation

BumbleB is a voice snippet\sound-bite search engine.

## Access and API Keys

#### Public Beta Key 
The BumbleB API is open to the public. We have instituted a simple, single public beta key system to let anyone try it out. The API key is required for all endpoints.

+ <b>The public beta key is "pl3tyKWdljSBr”</b> 
	
Please use this key while you develop your application and experiment with your integrations. Note: the public key is subject to rate limit constraints and we do not encourage live production deployments to use the public key.

#### Request a Production Key
Once you’re ready to use the BumbleB API in production, please send us an email to [api@bumbleb.io](mailto:api@bumbleb.io) to request a production API key. In your submission, please be prepared to provide the following:

+ Your app name with brief description, web / app store links, etc.

+ The 'live date' of the app and feature that integrates with the API. Briefly describe how the BumbleB API integrates with your app and provide screenshots of the implementation.

+ We require all apps that use the BumbleB API to conspicuously display "Powered By BumbleB" attribution marks where the API is utilized. Please provide screenshots of your attribution placement.

If you have any questions please feel free to contact us at [api@bumbleb.io](mailto:api@bumbleb.io). Please submit API corrections via [github issues](https://github.com/bumbleb/BumbleB-API/issues). Please see our [terms of service](http://bumbleb.com/terms) for any restrictions on using the service. We also recommend using the JSONview plugin for [Firefox](https://addons.mozilla.org/en-us/firefox/addon/jsonview/) or [Chrome](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en) to view the API responses in your browser. 

## Overview

The [BumbleB API](http://api.bumbleb.io) provides the following JSON endpoints:

+ search
+ sound by id
+ sounds by id 
+ trending

The Soundy API implements a REST-like interface. Connections can be made with any HTTP enabled programming language.

The BumbleB API implements a REST-like interface. Connections can be made with any HTTP or HTTPS enabled programming language.

###### Host

    api.bumbleb.com

###### Parameters

+ api_key - The public beta key is <b>"pl3tyKWdljSBr"</b>

## Search Endpoint

Search all Soundy voice snippets\sounds for a word or phrase. Punctuation will be stripped and ignored. Use a plus or url encode for phrases. Example honey+im+home.

Search all BumbleB voice snippets\soundbites for a word or phrase. Punctuation will be stripped and ignored. Use a plus or url encode for phrases. Example [honey+im+home](http://api.bumbleb.io/v1/sounds/search?q=honey+im+home&api_key=pl3tyKWdljSBr)   

[honey+im+home](http://api.bumbleb.io/v1/sounds/search?q=honey+im+home&api_key=pl3tyKWdljSBr&limit=1&offset=0) search query.

###### Path

    /v1/sounds/search

###### Parameters

+ q - search query term or phrase
+ api_key - the api key
+ limit - (optional) number of results to return, maximum 100. Default 25.
+ offset - (optional) results offset, defaults to 0.

### Sample Response, Search

    {
    "data": [
        {
            "type": "sound",
			"id": "6c0731b4b277e07c75927b53bb8793e2",
			"title": "The Thirteenth Floor",
			"transcription": "Hi honey, I'm home.  Did you miss me?",
			"duration": 4,
			"import_datetime": "2015-09-19T14:58:35.863+00:00",
			"release_datetime": "1999-05-28",
            image: {
                    "url": "http://ia.media-imdb.com/images/M/MV5BMTQ1NzEwNjM0OF5BMl5BanBnXkFtZTYwNTI4MDk5._V1_SX300.jpg",
					"width": 147,
					"height": 225
            },
             sounds:{
                 wav:{
                    "url": "https://s3.amazonaws.com/bumbleb/6c0731b4b277e07c75927b53bb8793e2.wav",
					"size": 51966
                 },
                 mp3:{
                    "url": "https://s3.amazonaws.com/bumbleb/6c0731b4b277e07c75927b53bb8793e2.mp3",
					"size": 51966
                 },
                 .... more formats
             },
        },
        ... 24 more items
    ],
    "meta": {
        "status": 200,
        "msg": "OK"
    },
    "pagination": {
        "total_count": 122,
        "count": 25,
        "offset": 0
    }
}



## Get Sound by ID Endpoint

Returns meta data about a sound, by sound id. In the below example, the sound ID is "6c0731b4b277e07c75927b53bb8793e2"

    http://api.bumbleb.io/v1/sounds/6c0731b4b277e07c75927b53bb8793e2?api_key=pl3tyKWdljSBr

[Example](http://api.bumbleb.io/v1/sounds/6c0731b4b277e07c75927b53bb8793e2?api_key=pl3tyKWdljSBr) get Sound by id query

###### Path

    /v1/sounds/<sound_id>


### Sample Response, Get Sound by ID

    {
		"data": [
			{
				"type": "sound",
				"id": "6c0731b4b277e07c75927b53bb8793e2",
				"title": "The Thirteenth Floor",
				"transcription": "Hi honey, I'm home.  Did you miss me?",
				"duration": 4,
				"import_datetime": "2015-09-19T14:58:35.863Z",
				"release_datetime": "1999-05-28T00:00:00.000Z",
				image: {
						"url": "http://ia.media-imdb.com/images/M/MV5BMTQ1NzEwNjM0OF5BMl5BanBnXkFtZTYwNTI4MDk5._V1_SX300.jpg",
						"width": 147,
						"height": 225
				},
				 sounds:{
					 wav:{
						"url": "https://s3.amazonaws.com/bumbleb/6c0731b4b277e07c75927b53bb8793e2.wav",
						"size": 51966
					 },
					 mp3:{
						"url": "https://s3.amazonaws.com/bumbleb/6c0731b4b277e07c75927b53bb8793e2.mp3",
						"size": 51966
					 },
					 .... more formats
				 },
			}
		],
		"meta": {
			"status": 200,
			"msg": "OK"
		}
    }
