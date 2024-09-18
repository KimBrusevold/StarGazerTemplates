# StarGazerTemplates

## Why


## Design

### Template definition
What a template should be able to do, and what it should look like is not set in stone and may change. To make the templating easier to recognize, I am inclined to use something similar to Razor/Blazor syntax. 

#### 1.
```html
<html>
<head>
</head>
<body>
<h1>Hello World</h1>
</body>
</html>
```
This is a valid template. Inserts no parameters into the template.

#### 2.

```razor
<html>
<head>
</head>
<body>
<h1>@(title)</h1>
</body>
</html>
```
Very similar to previus exmaple, but takes in parameter "title". When generating this template, you must provide a string as a parameter. When generating the template, you would call render method something like this:

```cs
Render("Hello World");
```
The returned string from render method would be the same as in the first example.

### Usage

The templates would exist in its own folder structure in the project. The folder may be called "Pages".
 
- program.cs
- MyWebApp.csproj
- Pages
 - Index.gazer
 - About gazer

In your minimal api, you should be able to render index template like this: 

(in this example the templates does not have any parameters. Could just be an ordinary html file)

```cs
//namespace is MyWebApp
var app = WebApplication.Create(args);

app.MapGet("/", () => MyWebApp.Pages.Index.Render());
app.MapGet("/about", () => MyWebApp.Pages.About.Render());

app.Run();
```
The templates are called as static methods in a static class.
