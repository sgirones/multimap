require 'rake/rdoctask'

Rake::RDocTask.new { |rdoc|
  rdoc.title    = 'Multimap'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.options << '--charset' << 'utf-8'

  rdoc.rdoc_files.include('README.rdoc')
  rdoc.rdoc_files.include('lib/**/*.rb')
}


task :default => :spec

require 'spec/rake/spectask'

Spec::Rake::SpecTask.new do |t|
  t.warning = true
end


begin
  require 'rake/extensiontask'

  Rake::ExtensionTask.new do |ext|
    ext.name = 'nested_multimap_ext'
    ext.gem_spec = $spec
  end

  desc "Run specs using C ext"
  task "spec:ext" => [:compile, :spec, :clobber]
rescue LoadError
end
