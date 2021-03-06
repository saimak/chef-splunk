require 'foodcritic'
require 'foodcritic/rake_task'
require 'rspec/core/rake_task'
require 'rubocop/rake_task'

desc 'Run RuboCop on the lib directory'
RuboCop::RakeTask.new(:rubocop) do |task|
  task.patterns = ['lib/**/*.rb']
  # only show the files with failures
  task.formatters = ['files']
  # don't abort rake on failure
  task.fail_on_error = false
end

desc 'Run Foodcritic lint checks'
FoodCritic::Rake::LintTask.new(:lint) do |t|
  t.options = {
    :fail_tags => ['any'],
    :tags => [
      '~FC003',
      '~FC015'
    ]
  }
end

desc 'Run ChefSpec examples'
RSpec::Core::RakeTask.new(:spec)

desc 'Run all tests'
task :test => [:lint, :spec, :rubocop]
task :default => :test
