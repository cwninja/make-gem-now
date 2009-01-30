require 'rubygems'
require 'rake'
require 'rake/testtask'
require 'rake/rdoctask'
require 'rake/gempackagetask'
require 'date'

spec = Gem::Specification.new do |s|
  s.name        = %q{make_gem_now}
  s.version     = "0.2"
  s.summary     = %q{A tool to build all gems in a given dir, and index them appropriately.}
  s.description = %q{A tool to build all gems in a given dir, and index them appropriately.}

  s.files        = FileList['[A-Z]*', 'lib/**/*.rb', 'test/**/*.rb', 'rails/*']
  s.require_path = 'lib'
  s.executables  = ["make-gem-now"]

  s.has_rdoc         = true
  s.extra_rdoc_files = ["README.markdown"]
  s.rdoc_options = ['--line-numbers', '--inline-source', "--main", "README.markdown"]

  s.authors = ["Tom Lea"]
  s.email   = %q{commits@tomlea.co.uk}

  s.platform = Gem::Platform::RUBY
end

Rake::GemPackageTask.new spec do |pkg|
  pkg.need_tar = true
  pkg.need_zip = true
end

desc "Clean files generated by rake tasks"
task :clobber => [:clobber_package]

desc "Generate a gemspec file"
task :gemspec do
  File.open("#{spec.name}.gemspec", 'w') do |f|
    f.write spec.to_ruby
  end
end
