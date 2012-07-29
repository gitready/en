desc "deploy site to gitready.com"
desc "Unpublish all posts"
task :unpublish do
  Dir["_posts/*.textile"].each do |post|
    puts "Unpublishing #{post}"
    lines = File.readlines(post)
    lines.insert(1, "published: false\n")
    File.open(post, "w") { |f| f.write lines.join }
  end
end

LANGS = %w[de en es fr he it ja ko nl pt-br ru sv]

desc "setup all branches"
task :setup do
  LANGS.each do |lang|
    system("git checkout -t -b #{lang} origin/#{lang}")
    system("git remote add #{lang} git@github.com:gitready/#{lang}.git")
  end
  system("git checkout en")
end

desc "publish to all branches"
task :publish do
  LANGS.each do |lang|
    system("git push #{lang} #{lang}:gh-pages")
  end
end
