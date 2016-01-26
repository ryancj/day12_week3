#Week 3 Day 12

###Sinatra
- Thin layer on top of rack gem
- gem install sinatra --no-ri --no-rdoc (no offline documentation)
- WEBrick because it is based on rack

###HyperText Transfer Protocol (HTTP)
- **REST** (most apis/sites use REST)
- Architecture style for networked applications
- REST uses four HTTP verbs
- Get, Host, Patch/Puts, Delete = display, create/add, update, delete
- HTTP response codes: 100(informational), 200(success), 300(redirectional),
400(client error), 500(server error)
- gem install sinatra-contrib --no-ri --no-rdoc
```ruby
name = params[:name]
"Hello #{name}"
```
- http://localhost:4567/greeting?name=Ryan (& to chain)
```ruby
#if your URL is: http://localhost:4567/greeting?name=Ryan&city=Burnaby
#params will be: {"name" => Ryan, "city" => "Burnaby"}
#params[:name] or params["name"]
```
- Dynamic URL
```ruby
#this is a dynamic url. It will match /greeting/anything
#for example: /greeting/john or greeting/hello
get "/greeting/:name" do |name|
  "Hello #{name} or Hello #{params[:name]}"

end
```
- Access by any HTTP interface "curl http://localhost:4567"

###ERB
- Templating system, built in for sinatra
- views folder in the app folder, inside: index.erb
```ruby
get "/" do
#this will render a template views/index.erb and sends it
#as a response (this is a Sinatra convention)
#erb is a ruby method (built-in with Sinatra) that takes in a first arguement
#which is a symbol that references a file name
  erb :index
end
```
- Ruby tags <% %>
- Hello **<%=** name **%>**, displays Ruby code
- ctrl+shift+.(with =), ctrl+.(just brackets), ctrl+shift+3(comments)
- @instance_variables for other files to access
- Use layout when you need to repeat your code
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My First Sinatra App</title>
  </head>
  <body>
    <%= yield %>
  </body>
</html>
```
- erb :greeting, layout: :app_layout 
