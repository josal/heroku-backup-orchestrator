desc 'Capture a new bundle for your heroku app and upload it to Amazon S3'
task :cron do
  require 'lib/heroku_backup_orchestrator.rb'
  
  HerokuBackupOrchestrator::BackupService.new.backup_all
end

desc 'Run unit tests'
task :test do
  require 'test/unit'
  
  test_dir = 'test'
  Dir.open(test_dir).each do |f|
    qualified_filename = File.join(test_dir, f)
    if File.file?(qualified_filename) && f.match(/_test.rb\z/)
      require qualified_filename
    end
  end
end

desc "The default task will invoke the 'test' task"
task :default do
  Rake::Task['test'].invoke
end