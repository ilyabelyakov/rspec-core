require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "rspec-core"
    gem.summary = "RSpec Core"
    gem.email = "dchelimsky@gmail.com;chad.humphries@gmail.com"
    gem.homepage = "http://github.com/rspec/core"
    gem.authors = ["David Chelimsky", "Chad Humphries"]
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end

rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'lib/spec/core/rake_task'
Spec::Core::RakeTask.new :spec do |t|
  t.pattern = "spec/**/*_spec.rb"
end

desc "Run all examples using rcov"
Spec::Core::RakeTask.new :coverage do |t|
  t.pattern = "spec/**/*_spec.rb"
  t.rcov = true
  t.rcov_opts = %[--exclude "gems/*,db/*,/Library/Ruby/*,config/*" --text-summary  --sort coverage]
end

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML.load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "rspec-core #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

