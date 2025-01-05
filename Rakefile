# frozen_string_literal: true

# :build
# :install
# :release
require 'bundler/gem_tasks'

# :clean
# :clobber
# :compile
# :compile:serialport
require 'rake/extensiontask'

CLOBBER << FileList['doc']
CLOBBER << FileList['pkg']

GEMSPEC = eval File.read File.expand_path('serialport.gemspec', __dir__)

Rake::ExtensionTask.new 'serialport', GEMSPEC do |ext|
  ext.lib_dir = File.join(*['lib', ENV.fetch('FAT_DIR', nil)].compact)
  ext.ext_dir = 'ext/native'
end

# add your default gem packing task
Gem::PackageTask.new(GEMSPEC) do |pkg|
end

task default: %i[clean clobber compile test]
