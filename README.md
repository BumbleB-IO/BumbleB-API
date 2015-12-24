# BumbleB API Documentation

BumbleB is a sound clip search engine.

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

If you have any questions please feel free to contact us at [api@bumbleb.io](mailto:api@bumbleb.io). Please submit API corrections via [github issues](https://github.com/bumbleb/BumbleB-API/issues). Please see our [terms of service](http://www.bumbleb.io/api-terms) for any restrictions on using the service. We also recommend using the JSONview plugin for [Firefox](https://addons.mozilla.org/en-us/firefox/addon/jsonview/) or [Chrome](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en) to view the API responses in your browser. 

## Overview

The [BumbleB API](http://api.bumbleb.io) provides the following JSON endpoints:

+ search
+ sound by id
+ sounds by ids 
+ trending

The BumbleB API implements a REST-like interface. Connections can be made with any HTTP or HTTPS enabled programming language.

###### Host

    api.bumbleb.io

###### Parameters

+ api_key - The public beta key is <b>"pl3tyKWdljSBr"</b>

## Search Endpoint

Search all BumbleB sounds for a word or phrase. Use a url encode for multiple phrases.

Example of a search query on the phrase [honey im home](https://api.bumbleb.io/v1/sounds/search?q=honey%20im%20home&api_key=pl3tyKWdljSBr).

	https://api.bumbleb.io/v1/sounds/search?q=honey%20im%20home&api_key=pl3tyKWdljSBr

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
                    	"url": "https://dhhymw1agiix5.cloudfront.net/tt0139809/poster.jpg"",
			"width": 147,
			"height": 225
            },
             sounds:{
                 wav:{
                    	"url": "https://d3fzkdiefbjnh9.cloudfront.net/55fd781c44616ec1c9000728.wav",
			"size": 51966
                 }
                 .... more formats if available
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

Returns a sound, by id. In the below example, the sound ID is "

[Example](https://api.bumbleb.io/v1/sounds/55fd781c44616ec1c9000728?api_key=pl3tyKWdljSBr) of a sound by id query

	https://api.bumbleb.io/v1/sounds/55fd781c44616ec1c9000728?api_key=pl3tyKWdljSBr

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
			"import_datetime": "2015-09-19T14:58:35.863+00:00",
			"release_datetime": "1999-05-28",
            image: {
                    	"url": "https://dhhymw1agiix5.cloudfront.net/tt0139809/poster.jpg"",
			"width": 147,
			"height": 225
            },
             sounds:{
                 wav:{
                    	"url": "https://d3fzkdiefbjnh9.cloudfront.net/55fd781c44616ec1c9000728.wav",
			"size": 51966
                 }
                 .... more formats if available
             },
        }
    ],
    "meta": {
        "status": 200,
        "msg": "OK"
    }
	}

## Trending Endpoint

Get BumbleB sounds that are currently most popular. You can get up to 100 sounds results.

[Example] (https://api.bumbleb.io/v1/sounds/trending?api_key=pl3tyKWdljSBr) of a trending query.

	https://api.bumbleb.io/v1/sounds/trending?api_key=pl3tyKWdljSBr

###### Path

    /v1/sounds/trending

###### Parameters

+ api_key - the api key
+ limit - (optional) number of results to return, maximum 100. Default 25.
+ offset - (optional) results offset, defaults to 0.

### Sample Response, Trending

	{
    "data": [
        {
            	"type": "sound",
		"id": "55c5cb7d44616e400f000331",
		"title": "Casino Royale",
		"transcription": "The name's Bond... James Bond.",
		"duration": 4,
		"import_datetime": "2015-08-08T09:27:25.607Z",
		"release_datetime": "2006-11-17T00:00:00.000Z",
		"source": "http://www.dailywav.com/",
		"image": {
			"url": "https://dhhymw1agiix5.cloudfront.net/tt0381061/poster.jpg",
			"width": 300,
			"height": 446
		},
		"sounds": {
			"wav": {
			"url": "https://d3fzkdiefbjnh9.cloudfront.net/55c5cb7d44616e400f000331.wav",
			"size": 19076
		}
	},
        ... 24 more items
    ],
    "meta": {
        "status": 200,
        "msg": "OK"
    },
    "pagination": {
        "total_count": 100,
        "count": 25,
        "offset": 0
    }
	}
