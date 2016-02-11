require 'travis/yaml'

config = Travis::Yaml.parse('language: ruby')
config = Travis::Yaml.parse(language: 'ruby')

config[:language] # ruby
config.language   # ruby

# using parse! instead of parse will print out warnings
Travis::Yaml.parse! deploy: []
# .travis.yml: missing key "language", defaulting to "ruby"
# .travis.yml: value for "deploy" section is empty, dropping

# have it generate the build matrix for you
Travis::Yaml.matrix('rvm: [jruby, 2.0.0]').each do |matrix_entry|
  puts matrix_entry.ruby
end
