desc 'Generate the self-contained application package for deployment.'
file 'application.tar' => ['application.rb', 'config.ru', 'vendor', 'Gemfile.lock'] do |t|
  sh "tar cf application.tar #{t.prerequisites.join(' ')}"
end

desc 'Vendor all the gems so we can package and deploy our application.'
directory 'vendor' => ['Gemfile', 'Gemfile.lock'] do
  sh 'bundle install --deployment'
end

desc 'Clean up all build artifacts.' do
  sh 'rm -r vendor application.tar'
end
