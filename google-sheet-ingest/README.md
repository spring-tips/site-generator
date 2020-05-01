# Spring Tips Site Generator 

This processor down and makes available as an RSS feed the latest information about all the published Spring Tips for ease of integration into other feeds. This is the canonical feed about which videos were published and when. 

The result of this processor is an RSS feed (`spring-tips.xml`) that other clients can in turn consume when updating other indexes. The output of this process [lives in on the web](http://SpringTipsLive.io/rss.xml). 

Perhaps one day it'll also generate a spiffy looking website. 

## Building 

Two files are required to build and run the application: `credentials.json` and `token.pickle`.

The first file, `credentials.json`, can be obtained by registering an application with Google Cloud. 
I have stored my particular version of this file in a Lastpass folder called `spring-tips-sheet`. You should do something (secure) with yours. Do _not_ check it into the code!  

If you run the program with only the first parameter present, it'll generate a `token.pickle` in the current directory. 
**But**, in order to do so, the program will open a browser and prompt you to approve the request. So, you'll need to do this on your local machine before running it in a headless environment.

The information in `token.pickle` is binary data, so I've run it through the following process:

```shell 
PICKLED_TOKEN=$( cat token.pickle | base64 ) 
```

In order to get this to work on Github Actions, I just copied the value to the clipboard and then pasted it into the `Secrets` section for my Github Actions as a new environment variable, `PICKLED_TOKEN`.  

```shell 
 cat token.pickle | base64 | pbcopy
```

I also created a new environment variable, `CREDENTIALS_JSON`, for the text data in the `credentials.json` file. 


   



