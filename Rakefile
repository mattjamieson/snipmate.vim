require 'rake'

dirs = Dir['**/']

desc "Install"
task :install do
  vimfiles = if ENV['VIMFILES']
               ENV['VIMFILES']
             elsif RUBY_PLATFORM =~ /(win|w)32$/
               File.expand_path("~/vimfiles")
             else
               File.expand_path("~/.vim")
             end

  puts "Installing snipmate.vim"
  dirs.each do |dir|
    Dir.new(dir).entries.reject { |file| not File.file?(File.join(dir, file)) }.each do |file|
      file = File.join(dir, file)
      target_file = File.join(vimfiles, file)
      FileUtils.mkdir_p(File.dirname(target_file)) unless File.exists?(File.dirname(target_file))
      FileUtils.cp(file, target_file)
      puts "  Copied #{file} to #{target_file}"
    end
  end
end

task :default => :install 
