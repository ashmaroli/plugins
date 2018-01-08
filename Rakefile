# frozen_string_literal: true

require "rubygems"
require "rake"
require "open-uri"
require "safe_yaml"

task :default do
  entries = SafeYAML.load_file("_data/entries.yml")
  entries.each do |type, list|
    FileUtils.mkdir_p("_data/#{type}")
    list.each do |item|
      begin
      data = open("https://rubygems.org/api/v1/gems/#{item}.yaml").read
      File.open("_data/#{type}/#{item}.yml", "wb") { |file| file.puts data }
      rescue OpenURI::HTTPError
        puts "#{item} does not seem to exist at rubygems.org"
        next
      end
    end
  end
end
