### The Beginning 

Well, for starters, it would probably help to have an account

visit [https://signup.heroku.com/](https://signup.heroku.com/) and create an account.

After that, you'll probably want to download the Heroku and Git CLIs

A CLI, or Command Line Interface, is a way for you to call certain commands from your terminal.

### Download Guide

#### Windows

[64 Bit installer](https://cli-assets.heroku.com/heroku-x64.exe)

[32 Bit installer](https://cli-assets.heroku.com/heroku-x86.exe)

#### Mac
Since you should already have homebrew and git installed, all you have to do is type:

> brew install heroku/brew/heroku

#### Ubuntu
Run the following in your terminal
 
> sudo snap install heroku --classic


### Accessing Heroku through the CLI

Now you're going to want to access your account from the terminal.

Just type

> heroku login 

And bam! You'll have access to all your projects from the terminal!

Now, we are going to create an entire heroku website through just the terminal! Be warned, this app is going to use Node.js in order to run, so run 

> node --version
and
> npm --version

in order to make sure you have everything properly installed
now that that is out of the way, run

> heroku create name-of-your-app

BAM! That easy!

Well not really, we still have more to go.

Let's create a couple files.

> git init
> npm init
> touch Procfile
> touch app.js 
> npm install express --save


Ok, great, we have everything we need in the file directory, we just have to append some stuff to the files. 
##### app.js
```
{
	var express = require('express');
	var app = express();

	app.get('/', function (req, res) {
		res.send('Hello World!');
	});
	
	app.listen(3000, function () {
		console.log('Example app listening on port 3000!');
});
}
```

##### Procfile
`web: node app.js`


### Launching our app!

This is the easiest part!

Just run a few commands such as

> heroku git:remote -a name-of-your-app
> git add .
> git commit -am 'first commit'
> git push heroku master
> heroku open

Bam! there's your app up and running!

