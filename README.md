# new_page_thesis

## Copy this code to the root of your project and save it in a .rb file
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

def new_template_setup(template_name, shared_content = false)
  if shared_content
    File.open("#{Dir.pwd}/app/views/custom/shared/#{template_name}.html.erb", "w")
    puts "#{template_name}.html.erb created."
  else
    File.open("#{Dir.pwd}/app/views/custom/#{template_name}.html.erb", "w")
    puts "#{template_name}.html.erb created."
    return
  end
end

def new_javascript_component(component_name, code)
  File.open("#{Dir.pwd}/app/assets/javascripts/components/#{component_name}.js", "w+") {|f| f.write("#{code}") }
  puts "#{component_name}.js created."
end

    
def multi_gets all_text=""
  while all_text << STDIN.gets
    return all_text if all_text["\n\n"]
  end
end

def start
  puts "What would you like to create?"
  puts "1. New Page"
  puts "2. New Template"
  puts "3. New Javascript Component"
  puts "3. Exit"
  answer = gets.chomp
  if answer == "1"
    puts "What is the name of the page?"
    page_name = gets.chomp
    new_page_setup(page_name)
  elsif answer == "2"
    puts "What is the name of the template?"
    template_name = gets.chomp
    puts "Is this a shared template? (y/n)"
    shared_answer = gets.chomp
    if shared_answer == "y"
      new_template_setup(template_name, true)
    else
      new_template_setup(template_name) 
    end
  elsif answer == "3"
    puts "What is the name of the javascript component?"
    component_name = gets.chomp
    puts "Paste your javascript in then hit ENTER twice."
    code = multi_gets
    new_javascript_component(component_name, code)
  elsif answer == "4"
    puts "Goodbye!"              
    exit
  else
    puts "Invalid input."
    exit
  end
  puts "Done!"
  puts "Would you like to create anything else?"
  puts "Type yes or no"
  new_answer = gets.chomp
  if new_answer == "yes"
    start()
  else
    puts "Goodbye!"
    exit
  end
end


start()
```
## In the terminal run `ruby fake_cli.rb` or `ruby [whatever_you_named_the_file.rb]`.
### Pass in the new page's name or a new template's name. Example: overview_a  ||  _custom_callout 
### All 3 pages [yaml.erb, js, and scss] will be created for you. Or a template will be created in the Custom Folder.
