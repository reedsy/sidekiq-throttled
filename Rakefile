# frozen_string_literal: true

require "bundler/gem_tasks"

require "rspec/core/rake_task"
RSpec::Core::RakeTask.new(:spec)

desc "Run RuboCop"
task :rubocop do
  require "rubocop"
  result = RuboCop::CLI.new.run([])
  abort("RuboCop failed!") if result.nonzero?
end

namespace :rubocop do
  desc "Auto-correct RuboCop offenses"
  task :autocorrect do
    require "rubocop"
    result = RuboCop::CLI.new.run(["--auto-correct"])
    abort("RuboCop failed!") if result.nonzero?
  end
end

default_suite = ENV["CI"] ? :spec : %i[spec rubocop]
named_suites  = { "rubocop" => :rubocop, "rspec" => :spec }

task :default => named_suites.fetch(ENV.fetch("SUITE", nil), default_suite)

desc "Build and push package to GitHub Packages"
task :release_github do
  Rake::Task["build"].invoke
  %x(gem push --key github \
   --host https://rubygems.pkg.github.com/reedsy \
   pkg/#{Bundler::GemHelper.gemspec.name}-#{Bundler::GemHelper.gemspec.version}.gem)
end
