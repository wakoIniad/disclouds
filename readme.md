# 1. Why use discloud
**By using discord, You can manage the data directly without using your strage**     
**Update: Increased storage / Improved speed.**

## table of contents

 - [HOW TO USE](#sample)
 - [INFOMATION](#infomation)
   - [updata](#updata)
   - [operating_environment](#operating-environment)
     - [language](#language)
     - [dependencies](#dependencies)
   - [about defects etc](#about-defects-etc)

# 2. How to use

### First
Please create new server only for this database

### Second
<details><summary>Sample Code</summary><div>

```js
(async function(){

    const cloud = require('disclouds');
    const DB = new cloud;

    /**
     * ::settings::
     * You can also configure by using DB.setting()
     */
    const DB = new cloud({
        //encode settings
        encode:{
            use:true,//encode = on
            key:{
                keyA:"(32 alphanumeric characters)",
                keyB:"(16 alphanumeric characters)"
            }
        },
        token:"Your token is here",
        server:"Your Server ID (This server id's server will be a database)"
    });

    /**
     * How to use encode
     */
    DB.encodOn();//enable encoding
    DB.setKey("(32 alphanumeric characters)","(16 alphanumeric characters)");//set key

    const client = await DB.create("Your token is here",{
        server:"Your Server ID (This server id's server will be a database)",
        //You can also set this way : DB.setServer("ID");
        name:"DataTable's name"
    }, {} //default value
    );

    client.on('error',err=>{
        console.log(err.message);//db client's error
    })

    client.on('ready',async ()=>{//client ready
        console.log('ready...');

        await DB.set("text")//set a data in the database
        .then(async()=>{
            console.log(await DB.get())
            //output: "text"
        }); 

        /**
         * set event
         */
        client.on('set',data=>{
            data = data[0];//body (data[1] is this process key)
            console.log(data.processTime);
            console.log(data.setData);
            console.log(data.info);
        });

        /**
         * get event
        */
        client.on('get',data=>{
            var info = data[0];
            //body
            var key = data[1];
            //process key
        });

        /**
         * writeEnd event
         */
        client.once('writeEnd',async ()=>{
            console.log(await DB.get());
        });

        DB.info();
        //You can get your db infomations
    });
})();
```
</div></details>

# 3. LICENSE
This software was released under the MIT License, Pleease check at LICENSE.txt.

## UPDATA
2020:10/10 **Significant improvement**  
2020:10/18 **Revised again**  
2020:11/14 **Significant weight reduction**  
2020:11/17 **Fixing a terrible mistake**


## Operating environment
### language
Node.js
### Dependencies
discord.js (very old version)

## About defects etc :email:
Contact
" wada.iniad@gmail.com "