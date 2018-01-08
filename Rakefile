# frozen_string_literal: true

require "rubygems"
require "rake"
require "open-uri"
require "safe_yaml"

task :default do
  data = SafeYAML.load_file("_data/entries.yml")
  data.each do |type, list|
    FileUtils.mkdir_p("_data/#{type}")
    list.each do |item|
      File.open("_data/#{type}/#{item}.yml", "wb") do |file|
        file.puts open("https://rubygems.org/api/v1/gems/#{item}.yaml").read
      end
    end
  end
end
