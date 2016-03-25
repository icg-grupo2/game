desc 'Tasks releated to build'
namespace :build do
  desc 'Build PDF doc from wiki'
  task :doc do
    WIKI_REPO='https://github.com/icg-grupo2/game.wiki.git'
    GAME_DIR='game.wiki'

    sh 'git', 'clone', '-q', WIKI_REPO if not Dir.exists?(GAME_DIR)
    files = Dir.entries(GAME_DIR)
    Dir.chdir(GAME_DIR);
    
    puts '--- Converting to PDF ---'
    files.each do |f|
      if f.match('(.)\.md')
        puts 'PDF: ' + f 
        sh 'markdown-pdf', f 
        sh 'mv', f.chomp('.md') + '.pdf', '../docs'
      end
    end
    Dir.chdir("..");
    Dir.delete(GAME_DIR);
  end
end
