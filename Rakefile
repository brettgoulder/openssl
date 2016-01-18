gem 'rake-compiler', '~> 0.9'

require 'rake'
require 'rake/extensiontask'
require 'rake/testtask'

Rake::ExtensionTask.new('openssl')

# the same as before
Rake::TestTask.new do |t|
  t.libs << 'test'
  t.warning = true
end

task :test => :debug
task :debug do
  sh "ruby -ropenssl -e 'puts OpenSSL::OPENSSL_LIBRARY_VERSION'"
end

task :sync do
  trunk = ENV.fetch("RUBY_TRUNK_PATH", "../ruby")

  sh "cp #{trunk}/ext/openssl/*.c #{trunk}/ext/openssl/*.h #{trunk}/ext/openssl/*.rb ext/openssl/."
  sh "cp -R #{trunk}/ext/openssl/lib/* lib/."
  sh "cp #{trunk}/test/openssl/test_*.rb test/."
  sh "cp #{trunk}/test/openssl/utils.rb test/utils.rb"
end
