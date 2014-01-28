require "bundler/gem_tasks"

require 'rspec/core'
require 'rspec/core/rake_task'

RSpec::Core::RakeTask.new(:spec) do |t|
  t.rspec_opts = ["-c", "-f progress", "-Ilib"]
  t.pattern = "spec/**/*_spec.rb"
  t.verbose = true
end
task :spec => :compile

require 'rake/extensiontask'
spec = Bundler::GemHelper.gemspec
Rake::ExtensionTask.new('linkedlist', spec) do |ext|
  ext.ext_dir = 'ext/linkedlist'
  ext.lib_dir = 'lib'
end

desc "gem reinstall"
task :reinstall do |t|
  system "gem uninstall list"
  system "rake clean"
  system "bundle exec rake"
  system "rake install"
  system "irb -rlist"
end


task :default => [:spec]
