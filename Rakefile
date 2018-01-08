# frozen_string_literal: true

require "rubygems"
require "rake"
require "open-uri"
require "safe_yaml"

task :default do
  data = SafeYAML.load_file("_data/entries.yml")
  puts data
  File.open("_data/jekyll.yml", "wb") do |file|
    file.puts open("https://rubygems.org/api/v1/gems/jekyll.yaml").read
  end
end
