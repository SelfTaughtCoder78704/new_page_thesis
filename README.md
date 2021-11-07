# new_page_thesis

# This tool can be added to the root of your project
## Copy This Code
```
# program to create new files in ruby and puts them in correct directory
def new_page_setup(page_name)
  File.open("#{Dir.pwd}/app/assets/javascripts/pages/#{page_name}.js", "w+") {|f| f.write("//= require jquery3
  //= require libs/tracking
  //= require static-shock/params") }
  File.open("#{Dir.pwd}/app/assets/stylesheets/pages/#{page_name}.scss", "w+")  {|f| f.write("@import '../company/*';
  @import 'base/base';
  @import 'base/sections/_section.linkbar';
  @import 'base/sections/_section.header';
  @import 'base/sections/_section.hero';
  @import 'base/sections/_section.footer';") }
  File.open("#{Dir.pwd}/lib/page_content/#{page_name}.yaml.erb", "w+")
  puts "#{page_name}.yaml.erb, #{page_name}.js, and #{page_name}.scss created."
  puts "The Yaml file was created empty, the Javascript and Stylesheet have enough to make the server work."
  return
end
puts "New page creation:"
puts "Enter the name of the page. Ex. overview_a"
page_name = gets.chomp
new_page_setup(page_name)
```
## In the terminal run `ruby fake_cli.rb` or `ruby [whatever_you_named_the_file.rb]`.
### Pass in the new page's name. Example: overview_a
### All 3 pages [yaml.erb, js, and scss] will be created for you.
