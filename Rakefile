#!/usr/bin/env rake
require "bundler/gem_tasks"

# RSpec
require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new('spec')
task :default => :spec

# Compile
namespace :aspm do
  desc "Parse PDF and generate files"
  task :generate do
    Dir['input/*.txt'].each do |file|
      currency = File.basename(file, '.txt')
      body = File.read file
      array = body.split(/\s/)

      amount = []
      amount_pro = []

      array.each_slice(2) do |slice|
        amount << slice.first
        amount_pro << slice.last
      end

      File.write("lib/prices/#{currency}", amount.join("\n"))
      File.write("lib/prices/#{currency}_pro", amount_pro.join("\n"))
    end
  end
end
