![Logo]
(https://raw.githubusercontent.com/jortechve/mixerjs/develop/imgs/logo.png)

Web server that **serves multiple JavaScript or CSS libraries in a single http request.** 
During web development, a project will need the use of different kind of libraries. It can be 
frameworks, plugins or tracking scripts. Some websites load these dependecies one http request at a time, this means 
as dependencies grow it creates an overhead on the performance of the website. To handle this, there are some continuous
integration tools for unifying and minifying files. But, theses tools takes time and knowledge to make proper use of 
them. Hopefully MixerJS will provide a easy solution for it. 


The basic use will be:

- http://hostname/filename.js?libraryA&libraryB

- http://hostname/mixer.js?libraryA=versionA&libraryB


* ##Installation
    
    To run mixerJS, you will need to install nodejs. Go to [their website](https://nodejs.org/download/) 
    for further instructions. Once installed, you can run the following command in the terminal:
    
    ```node mixer.js```

* ##How It Works
    Mixerjs uses [bower](http://bower.io/) for fetching the necessary libraries and does some underneath logic to handle 
    library dependency and errors. It uses different tools for minifying, concatenating and making custom builds.

* ##Configuration File
    MixerJs will have by default some basic configuration.
    
    **config.json**
    
    
    ```JSON
    {
        "env"    : "develop",
        "port"   : 8080,
        "builds" : [],
        "cache"  : false
    }
    ```
    
* ##Features
     
    + ####Minifying
     
     Minifying the libraries can be optional. Adding .min.js or .min.css to the end of the filename will minify it 
     automatically.
     
    + ####Custom builds
     
     Some libraries allows to create custom builds in order to just take what you need. MixerJS can accept a json 
     structure through the query for that specific library. More information in 
     [builds](https://github.com/jortechve/mixerjs/customBuilds)   
        
    + ####Cache and nginx
     
     For better use of MixerJS, we can take advantage of nginx cache. Nginx cache is very fast, with either memcache 
     or disk storage. The first attempt to retrieve the file will go through nginx and it will be proxied to mixerJS. 
     Subsequent attempts will be serve by nginx's cache. 
     
* ##Testing TODO
     
     MixerJS have some test you can run by using mocha. To run the tests, go to the terminal and do:
     
* ##Demo
     We have set up a small server using the domain name `jort.ch`, so you can check it online. Some uses are:
     
    **JS**
    
     + http://jort.ch/mixer.js?jquery
     + http://jort.ch/mixer.min,js?lodash=2.5&jquery
     + http://jort.ch/compile.js?lodash=%7B%22category%22%3A%22array%22%2C%22plus%22%3A%5B%22random%22%2C%22template%22%5D%7D
     
    **CSS**
    
     + http://jort.ch/mixer.css?boostrap
     + http://jort.ch/mixer.css?jquery&foundation