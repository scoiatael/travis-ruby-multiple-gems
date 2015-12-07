require 'pathname'
require 'bundler'

task :default do
  Dir['gems/**/spec'].each do |dir|
    path = Pathname.new(dir)
    gem_root = path.dirname

    puts '---'
    puts "Processing #{gem_root}"
    puts '---'

    Bundler.with_clean_env do
      system("bundle install --gemfile=Gemfile", chdir: gem_root, out: '/dev/null')
      system("bundle exec rspec -f doc", chdir: gem_root)
    end
  end
end
