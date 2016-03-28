require 'html-proofer'

SITE_DIR = './_site'

def jekyll(cmd)
  sh "bundle exec jekyll #{cmd}"
end

def build_site
  jekyll 'clean'
  jekyll 'build'
end

'Run the Markdown specs and HTML Proofer'
task :ci do
  build_site
  HTMLProofer.check_directory(SITE_DIR, cache: { timeframe: '2w' } ).run
end

'Run the site locally on localhost:4000'
task :dev do
  build_site
  jekyll 'serve --watch --drafts'
end

'Build the site in ./_site'
task :build do
  build_site
end


task default: :ci
