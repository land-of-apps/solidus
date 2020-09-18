# frozen_string_literal: true

source 'https://rubygems.org'

group :backend, :frontend, :core, :api do
  gemspec require: false

  gem 'appmap', github: 'applandinc/appmap-ruby', branch: 'master'

  rails_version = ENV['RAILS_VERSION'] || '~> 5.2.0'
  gem 'rails', rails_version, require: false

  # Temporarily locking sprockets to v3.x
  # see https://github.com/solidusio/solidus/issues/3374
  # and https://github.com/rails/sprockets-rails/issues/369
  gem 'sprockets', '~> 3'

  platforms :ruby do
    case ENV['DB']
    when /mysql/
      gem 'mysql2', '~> 0.5.0', require: false
    when /postgres/
      gem 'pg', '~> 1.0', require: false
    else
      gem 'sqlite3', require: false
      gem 'fast_sqlite', require: false
    end
  end

  platforms :jruby do
    gem 'jruby-openssl', require: false
    gem 'activerecord-jdbcsqlite3-adapter', require: false
  end

  gem 'database_cleaner', '~> 1.3', require: false
  gem 'factory_bot_rails', '~> 4.8', require: false
  gem 'rspec-activemodel-mocks', '~>1.1', require: false
  gem 'rspec-rails', '~> 3.7', require: false
  gem 'simplecov', require: false
  gem 'with_model', require: false
  gem 'rails-controller-testing', require: false
end

group :backend, :frontend do
  gem 'capybara', '~> 2.15', require: false
  gem 'capybara-screenshot', '>= 1.0.18', require: false
  gem 'selenium-webdriver', require: false
  gem 'poltergeist', '~> 1.9', require: false
end

group :frontend do
  gem 'generator_spec'
end

group :backend do
  gem 'teaspoon', github: 'jejacks0n/teaspoon', require: false
  gem 'teaspoon-mocha', github: 'jejacks0n/teaspoon', require: false
end

group :utils do
  gem 'pry'
  gem 'launchy', require: false
  gem 'i18n-tasks', '~> 0.9', require: false
  gem 'rubocop', '~> 0.53.0', require: false
end

gem 'rspec_junit_formatter', require: false, group: :ci

# Documentation
gem 'yard', require: false, group: :docs

custom_gemfile = File.expand_path('Gemfile-custom', __dir__)
eval File.read(custom_gemfile) if File.exist?(custom_gemfile)
