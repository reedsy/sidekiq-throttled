# frozen_string_literal: true

source "https://rubygems.org"

gem "appraisal"
gem "rake"
gem "rspec"
gem "sidekiq", "< 7"

group :development do
  gem "byebug"
  gem "guard",         :require => false
  gem "guard-rspec",   :require => false
  gem "guard-rubocop", :require => false
end

group :test do
  gem "apparition"
  gem "capybara"
  gem "puma"
  gem "rack-test"
  gem "sinatra"
  gem "timecop"
end

group :lint do
  gem "rubocop",              :require => false
  gem "rubocop-performance",  :require => false
  gem "rubocop-rake",         :require => false
  gem "rubocop-rspec",        :require => false
end

# Specify your gem's dependencies in sidekiq-throttled.gemspec
gemspec
