#Getting Started

#Building a Simple Web Page

####This guide walks you through the process of creating a "hello world" endpoint using Brute.io

###You'll need:
- A text editor would suffice
- Go 1.8 or later
- Install the Brute Web Engine
- Import the Brute front-end library
- 15 minutes of your time

###Guide in completing this guide (no pun intended)

Most likely for some developers, you may bypass some of the basic setup such as installing an IDE, installing the Go environment, etc. Either way, you will end up with a working Brute code

To install Brute.io, you can either install directly through `curl` with `sh` or build it from scratch by pulling the official Brute.io code from GitHub.

If you're on Mac OS, you can install Brute.io through `brew`. Simple executing the command `brew install brute.io`.

###Creating your Brute.io Web App Project

On your terminal, ensure that you are in the correct working directory of your choice. Then make a directory as your project folder, let's say `my-project`. Go to your created folder and execute the command:
`brute add endpoint`
A sequence of prompts will guide you how you want your first endpoint to setup. First it asks you to name the project if you haven't so. Second it will ask you whether to create a route. In this case, type `Y` and hit enter. Then, it will ask you to name your route and give its path. In that case, use the name `sample-page` and use the path `/greeting`. You may finish the process by responding `n` when it asks whether to continue creating more routes. Brute.io will finalize your project folder with endpoints and your `.brute.yml` configuration file.

###Creating your first endpoint

Your endpoint is your controller. A page is generated within the `Endpoint()` function. Whatever code is being invoked in the endpoint, the web server listens for any buffered data to deliver the data to your audience. 

Do not stress with the setting the content type of your page. Brute.io knows what type of content you are delivering. If brute.io notices you are streaming a different format, Brute.io will not set the content type to `text/html`. Brute.io will check the entire streamed data's syntax format whether any content matches `application/json` format, otherwise they are treated as `application/octet-stream`.

To create your endpoint, Brute.io had already creating your endpoint for your when you have created your web app project. Still if you want to create an additional endpoint, go to your web project's directory and simply execute the command:
`brute add endpoint -name="another-page" -path="congratulations"`

###Access your endpoint source code

In Brute.io, you are not actually creating web pages in pure HTML format. Although you can serve HTML pages by placing them in the static folder in your web app project directory but for the purposes of this guide, we'll walk through how to create an HTML page using HTML semantics written in Go.

When you create your endpoint, you'll notice that a directory is created in the `endpoints` folder in your web app project folder. The name of that particular directory is the name you have supplied from the command parameter `-name` or when you supplied it while in the interactive prompts.

Go to your generated endpoint directory and access the `main.go` source code. Inside the source code has a predefined method `Endpoint(args map[string]string)`. It is, simply by its name, the endpoint of your path that you have supplied alongside of the endpoint creation. In this case, when you access `http://localhost:8080/greeting`, the `Endpoint` method will be called in the Brute.io runtime environment. As of now, nothing impressive is displayed yet.

###Creating your first page in HTML

In your `Endpoint` method, simply create a hello world in paragraph enclosed with a `div` by doing:

```go
func Endpoint(args map[string]string) {
	Div().Value(func() {
		Paragraph().Value("Hello World!")
	})
}
```

Save your endpoint source code and go back to your terminal. Access your web app project's root directory and execute the following command:
`brute`

At this point, Brute.io is compiling your project and attempts to run the environment. Errors will be reported mainly your endpoints, if any. Errors such as unused imports, variables, and other syntax errors. With the Go programming language, it's easy to spot semantic errors.

Once you see the terminal output that says `You're on stage`. That means that you can access your page at `http://localhost:8080/greeting`. The page should display "Hello World!" given you have followed this guide correctly.

When you see the expected results, congratulations you have just created your first web page using Brute.io!

You can edit your source code and save it. Brute.io will automatically refreshed your newly edited page without restarting Brute.

###Summary

As you might find this a surprise, there are no added configurations after your page is displayed. This is because Brute.io will generate any trivial tasks such as supplying your page's CharSet. Brute.io fully prepares your page in HTML5. The next guides will advance you how to create dynamic pages using Brute.io.