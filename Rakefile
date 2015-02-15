require "rake"

desc "Install the dot files and config files"

task :install do
  Dir['configs/*'].each do |file|
    dotfile = file[8..-1]
    puts "linking ~/.#{dotfile}"
    backup "$HOME/.#{dotfile}"
    system %Q{ln -s "$PWD/#{file}" "$HOME/.#{dotfile}"}
  end

  puts "linking file in Library"
  (Dir['Preferences/*'] + Dir['Application\ Support/*']).each do |file|
    puts "linking #{file}"
    backup "$HOME/Library/#{file}"
    system %Q{ln -s "$PWD/#{file}" "$HOME/Library/#{file}"}
  end
end

def backup(file)
  system %Q{rm -rf "#{file}.bak"} rescue nil
  system %Q{mv "#{file}" "#{file}.bak"} rescue nil
end
